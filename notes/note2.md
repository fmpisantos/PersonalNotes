# Stays for marketing export

## Create batch

Since the export refers to guest who have already left, the export must be created for dates in the past.
Only guests who have a post stay email address are included in the export.

## Configuration

To configured the fields that will be exported the following registries can be adusted:

### Body

- class: staysinmarketing
- value: header
- description: Header for the export file
- possible values: 
    - defaults: OBJID;HN;HNAME;HSTREET;HCITY;CN;SN;STREET;COUNTRY;REGION;ADRESS;ZIP;CITY;DOB;ROOM;ARRIVAL;DEPARTURE;GENDER;EMAIL;TITLE;RES-NO;GDS-NO;MC;SOURCE;MEDIUM;CHANNEL;NN1;LANGUAGE;POST-STAY-ID;POST;RES-CREATION;SALES-DATE;PRICE-SEGMENT;PRICE-CATEGORY;SERVICEID;SERVICECODE;ROOMNIGHTS;ROOM-CATEGORY;QUALITY-FLAG
    - if hotel uses complex: COMPLEX;COMPLEX-DESC
    - optionals: PHONE-NUMBER;MOBILE-NUMBER

### Body mapping gender

- class: staysinmarketing
- value: bodymappinggender
- description: Renaming of gender values
- example: 
    - "M=Male;F=Female;X=Other"

### Header

- class: staysinmarketing
- value: header
- description: Header for the export file
- possible values: 
    - defaults: OBJID;HN;HNAME;HSTREET;HCITY;CN;SN;STREET;COUNTRY;REGION;ADRESS;ZIP;CITY;DOB;ROOM;ARRIVAL;DEPARTURE;GENDER;EMAIL;TITLE;RES-NO;GDS-NO;MC;SOURCE;MEDIUM;CHANNEL;NN1;LANGUAGE;POST-STAY-ID;POST;RES-CREATION;SALES-DATE;PRICE-SEGMENT;PRICE-CATEGORY;SERVICEID;SERVICECODE;ROOMNIGHTS;ROOM-CATEGORY;QUALITY-FLAG
    - if hotel uses complex: COMPLEX;COMPLEX-DESC
    - optionals: PHONE-NUMBER;MOBILE-NUMBER

### Header mapping

- class: staysinmarketing
- value: headerMapping
- description: Renaming of headers
- example: 
    - "OBJID=GUEST-OBJID;HN=HOTEL-NR"

### Omit header

- class: staysinmarketing
- value: omitHeader

### Path

- class: staysinmarketing
- value: path

### File prefix

- class: staysinmarketing
- value: filePrefix
- default: stays

### Coding

- class: staysinmarketing
- value: useUTF8

### Date format

- class: staysinmarketing
- value: dateformat
- default: ISO8601
