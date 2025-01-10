!TODO

# Barbers

## Tasks:
1. Price fluctuation base on special occasions/high demand
2. Lista de penteados na moda
3. Past cuts
4. Barber product recommendation

### 1. Price fluctuation base on special occasions/high demand
#### How to store
- [ ] New table
    - [ ] `EstablishmentServiceId`
    - [ ] `Price`
    - [ ] `DateTime-From`
    - [ ] `DateTime-To`
    - [ ] `Enabled`
    - [ ] `Establishment`
    - [ ] `Employee`
#### How to retrieve
Get method that is called everytime the price is retrieved from the data base (this should be cached)
#### Price needs to be saved by appointment
If the price can variate depending on the time that the appointment is made then the price needs to be saved in the appointment table
##### Ways to implement retrival
1. Update all repository queries that retrive price
2. Create a new method that retrieves the price that is called by every service where the price is being returned
3. Create a generic interface/class that can be extended by the DTOs that need the price
4. Create a new class that will represent the prices and has a to string/to double method so that spring can create a json double from it and load a json double to it. Note that this needs to take mapper into account to see if it works
###### 1. Update all repository queries that retrive price
- [ ] List methods that retrieve price from DB
    - EstablishmentServiceRepository:
        - findAll
        - findByEstablishmentId
        - findAllServiceDTO
        - listServices
    - EstablishmentService
        - updateService
        - getService
- [ ] List DTOs that use price
    - EstablishmentServiceBaseDTO
    - EstablishmentServiceDTO
    - ServiceDTO
    - ServiceFullDTO
    - ServiceListDTO
    - CreateServiceDTO
    - CreateEstablishmentServiceDTO
###### 4. New price type
- [x] Create new class
- [x] See how to make json work with it as a double
- [x] See how to make modelMapper work with it as a double
- [ ] Create method that retrives and caches the actual price from the db
- [ ] Create set and get methods that uses new method to retrieve the price

#### Front end methods that require the new price
- Get available days
- Get employee that can perform the service on a certain day
- Get available hours?
- On appointment creation

#### Methods to change
- [x] EstablishmentsController (when date is available)
    - listEmployeesOfEstablishmentService
    - GetServices
- [x] ServicesController
    - listDynamicPrices
- [x] SchedulesController
    - ~~listSchedules~~ (This would make the request that is already "slow" even slower, so this can be used in combination with other requests to get the actual price for the given days [concurrently])
    - listSchedulesByDay
- [x] AppointmentsController (when the date/newDate is under dynamic price adjustments)
    - create

#### How to retrieve the price
```sql
SELECT new com.teamsantos.easybarber.DTO.NameIdImagePriceDTO(
    e.employee.id,
    e.employee.employee.user.name,
    img.data,
    CASE
        WHEN dpe IS NOT NULL THEN dpe.price
        WHEN dp IS NOT NULL THEN dp.price
        ELSE e.service.price
    END
)
FROM EstablishmentServiceEmployee e
JOIN EmployeeSchedule es ON es.employee.id = e.employee.id AND es.establishment.id = e.establishment.id
LEFT JOIN e.employee.employee.images img ON img.isMain = true
LEFT JOIN e.dynamicPrices dpe ON dpe.from <= :date AND dpe.to >= :date
LEFT JOIN e.service.dynamicPrices dp ON dp.from <= :date AND dp.to >= :date
WHERE e.service.id = :establishmentServiceId
GROUP BY e.employee.id, e.employee.employee.user.name, img.data
```

#### Client changes
- [x] List of employees when the day is already selected should show the updated price if that price has been updated
- [x] On get available days of the month we need to also make a request to know the days of the month that have had price adjustments
- [x] Paint the available days that have had price adjustments with a different color
- [x] Display a background color on the days in the calendar that have received a price adjustment
- [x] On a day selection that has had a price adjustment show a banner with the new price and the reason for the price adjustment
- [x] On scheduling a new appointment that has had a price adjustment show a alert that the price has been adjusted (message in the response) and ask for confirmation that the user still wants to keep the appointment (this should only happen on availabilityScreen, not on the employeeselection)
- [x] Implement way to create/delete/update dynamic prices
- [ ] Fix problems in tests
- [ ] Implement tests for the new functionality

#### How do we want the price increases to beahave
- Price increases can be establishment wide or by employee. This means: 
    - When selecting the day and time of a service the employee might not yet be selected and therefor we might have price increases just for the employee that will endup being selected.
        This is hard to display on the application. 
        ##### Solution
        If the employee is selected we get the establishment wide and employee price increases to alert the user, and display the special prices per employee on the employee selection screen., and display the special prices per employee on the employee selection screen., and display the special prices per employee on the employee selection screen., and display the special prices per employee on the employee selection screen.       If the employee is not selected we only get the establishment wide price increase to alert the user, and display the special prices per employee on the employee selection screen.

#### Where was I:
Create new methods to create/delete/update dynamic prices