!TODO

# Dynamic Pricing

## Requirements
- Being able to set dynamic pricing for services by employee or establishment wide.

## Concequences
- Appointments now need to store the pricing of the service when it was scheduled.
- List of services by establishment or employee need to take the dynamic pricing into account (Only possible to see if )
- List of employees might need to show the price of the service because it might differ from employee to employee.
- List of services by establishment need to be able to have highest and lowest price for each service(this might make the list of services by establishment a bit more complex/slower) (this should only be taken into account if we have a date selected)
- Alert we should somehow alert the user that the price of the service has been increase do to the amount of scheduled appointments for that day.

## Problems
- Design: 
    - We dont know the date that the service will be scheduled so we dont know if the price has been dynamicly changed.

### Possible solutions
- We could display the dates the price by near the date on the calendar. This would need to be designed in a way that it is readable and there should be a an alert on the day selection that for x reason the price of the service on this day will be X.
- We could mark the days that the price of the service has been increased with a different color on the calendar. And on the day selection we could show the price and reason for the price increase in a top banner.

## Explanation
Para termos precos a atualizar dinamicamente para certas datas ou com quando x amount of slots are available precisamos de mostrar ao cliente que esta mudanca de preco existe.
Como o nosso appointment flow é: 
Establishment selection -> Service selection -> Employee selection -> Date selection -> Time selection -> Confirmacao do appointment
Ou
Establishment selection -> Service selection -> Date selection -> Time selection -> Employee selection -> Confirmacao do appointment
Nós não sabemos a data que o servico vai ser agendado até ao passo de confirmacao do appointment. Por isso temos de mostrar ao cliente que o preco do servico foi alterado para o dia que ele esta a selecionar.
A unica ideia de como mostrar isto na minha opiniao é no calendario marcar os dias com diferentes precos com uma cor diferente para os clientes saberem que algo é diferente nesse dia. 
E quando tocam no dia mostrar um banner com o preco e a razao da mudanca de preco.

## TODO: 
- [ ] List of services when the day is available needs to take into account dynamic pricing
- [ ] On get available days of the month we need to return if there was a price increase
- [ ] A new alert that the selected day is under price increases (This can be achieved by the getAvailableDaysOfTheMonth and client side coding)
- [ ] There needs to be a way to set a % of appointments in a day from which the price will increase
- [ ] There should be a way to set a new price for the day by service and across services