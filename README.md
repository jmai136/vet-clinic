# Vet Clinic 

## AUTHORS 
Isaac Madrigal, 
Jude Mai, 
Yareni Perez, 
Rayleen Richards 

## LIST OF TABLES 
### PET OWNER DETAIL 
I used int for my id because it takes up less space than a varchar, not only that but it would be able to auto increment and would ensure that no Id is repeated and or having different data other than numerical. For strings I chose NVarchar because since we are a vet clinic it would be safe to assume that there would be customers that might use special characters to properly spell their names, for example spanish speakers. I chose dateshort for dates because it can hold specified dates and a time is not required. In addition it also takes up less space than if I were to just put the date as string data type instead. -Yareni

### PET DETAILS 
If the point of a vet clinic is to provide service for pets, then it makes sense to have details about the pet in the system. The pet ID is an int that will be auto-incremented, which provides a unique identifier but is also convenient because the system will create a new identifier (auto-incrementation). The name is an NVarchar because it's possible to have foreign names. Weight is necessary because it could be a symptom of an illness if it is too high or low. Decimal is used for precision purposes,it is exact. Having the birth date determines the age of the pet, which allows the doctor to keep in mind what to look out for as it gets older, it makes sense to use a short date. Species and breed are self explanatory, certain species and breeds get different illnesses and some have long names. Sex is an enum because it's possible to have male, female, or intersex creatures. Health is an enum because it is a scale ranging from worst to best, and the description below is meant to allow the doctor to input in notes. There is a foreign key for the owner ID because we want to know what pet has what owner. -Jude 

### CLINIC DETAILS 
The Details is where the clinic is located. Using the Clinic ID and setting it as an enum because that will be the name and it will be constant. For name through city, we used NVarchar because there are names, addresses and cities that use special characters like the ones in Spanish. For the state we used characters and limited it to 2 because the abbreviation would be just enough to let us know what state. WA, CA, OR, ID, etc. Zipcode is limited to 5 characters and is a Char value because zipcodes only have 5 numbers. -Isaac 
 
### CLINIC DOCTOR DETAILS 
For clinic doctor details, the Doctor ID is in varchar. This is because we don’t plan on writing the doctors name but instead giving them an ID to work by. Name through city are once again Nvarchar to take care of any special characters that may pop up in names or address. Such as San Josè, the E is accented or in Hōnaunau. Phone number is in NVarchar because of the hyphen in between the numbers and the parenthesis. It is also limited to 12 so people don’t put more than they need to. Direct deposit is binary because Doctors either have direct deposit or they don’t. Then Routing number and account number are both Char values limited to 9 and 10 respectively. These types are nullable just in case we don’t use them as doctors do not need direct deposit. -Isaac 

### PET VISIT DETAILS 
The pet visit details is meant to be a bridge table and acts to make sure that the system maintains as much modularity as possible, aka, the main hub. The intention is that if someone were to look at the system, the first thing they should look at is this table, and from there if they want more detail, head to the other tables. Each visit has its own ID in order to keep track of what visits are which, it is a varchar because the goal is to have a code that's unique. Most of this table composes of foreign keys to the ids of the other tables as it is the connector between all of them. We use their IDs in order to not violate 3NF, as the goal is to make sure we keep information that belongs to that category in that category, and grab the address if necessary (i.e. forward declaration of another class). In terms of what is unique to the pet visit details table, the date of visit is a date short because we want the date, the diagnosis is an NVarchar because the doctor will be the one diagnosing, and it's possible for it to contain non English characters. A follow up is a yes or no question, and that is why we have a binary. -Jude 

### TREATMENT 
I did the treatment table. The primary key is the treatment ID which connects to the foreign key treatment ID on the pet visit details. It is nvarchar because English is not the only language and there are special characters in other languages. Treatment type is nvarchar as well because there are special characters in other languages that we may need to put in. The cost is going to be in money, because that’s the only way to figure out the cost without rounding to the nearest whole number. -Isaac 

### PRESCRIPTIONS 
For my prescriptions table I again chose ints for id because it takes up less space and is an efficient way to have auto incremented id. It also allows for unique id. Again I used date short for dates because it allows the date to be easily stored without the complications of time and other things. For instructions I decided to use nvarchar again because our customers could speak different languages and different languages sometimes require the need for special characters renewal I decided to go with binary because this would be an easy way to store yes or no data. For dosage I went with a decimal because dosages sometimes require have points and such so decimal would ensure that no amount is lost. -Yareni 

### MEDICATION 
For my medication table I again chose ints for id because it takes up less space and is an efficient way to have auto incremented id. It also allows for unique id. For my medication name I used varchar max because I know medication names can get lengthy and I would like to be on the safe side and allow enough room for a medication name to fit. For my medication description I used varchar because I would assume that this information would be in a primary language and would not need special characters. For the price I used money because this data type is meant for currency, in addition it would ensure that no money is lost. -Yareni 

### DR PAYROLL
The importance of adding a doctor payroll is to make sure that the doctors get paid properly, there needs to be a structure keeping track of that. One payroll is for many clinic doctors, because there is one payroll for many employees. The payroll ID is a varchar because the identifier is intended to be unique. With the bank name, addess lines, city, state, and zip, they are all varchar/nvarchar because there is no math done with them. The name, address lines, city might be long, however with the state and zip, we have abbreviations and know that zipcodes are from 5 to 9 numbers, it's unncessary to have 9 in this case. Routing and account numbers are 9 to 10 characters because that's how it is typically, and phone numbers have a set range too. -Jude 

### ACCOUNTS RECIEVABLE 
For the accounts receivable table I used varchar for my id types because it would allow me to create more unique id that would be able to have letters and numbers mixed in. For amount due I used money because this data type is meant to handle currency’s and would ensure that no money is lost. For paid I used binary because it would allow me to store a simple yes or no answer that would take up less space. -Yareni 

## PRESENTATION LINK 
[link to Google Slides Presentation made by lucid chart]([https://docs.google.com/presentation/d/12YfVAwFF7ExGGNaMwKP4DxIhIKLSXIY65-16OB-2_8k/edit?usp=sharing](https://docs.google.com/presentation/d/11-CiRru1nwJIIA33o_FDRnCbR4q9ms2DvTIvCe_GZJE/edit?usp=sharing))

[link to Lucid chart Diagram](https://lucid.app/lucidchart/53d0d32e-c37e-4253-8818-f19767c77935/edit?viewport_loc=-883%2C267%2C2386%2C861%2C0_0&invitationId=inv_fedce827-80c5-46a2-8e9f-81e3d1329d23)

////For Dan//// If you don't have a lucid chart account, I can send you my school credentials to get in  -Rayleen 

### 3NF FULFILLED 
If the goal of 3NF is promoting modularity and making sure there isn’t duplication and separation of data in correct categories, we have achieved it. The only way that the tables have access to other data in other tables is via the IDs of those tables, ensuring that everything associated with those tables is encapsulated. For instance, in our bridge table, we only have a reference to Pet ID, and not Owner ID because Owner ID is already part of the Pet Details table and therefore it’s possible to have a mismatch in our bridge table if we add columns for both. To think of it another way, it can be thought of as similar to forward declaration. If you have class A referencing class B, you’d declare class B, but you wouldn’t create a variable for class B inside class A. Or you can think of it as you have person A and person B, person A might be next to person B and using them to scan for healthy organs, but person A should not be ripping out an organ from person B to sell it on the black market, because that’s illegal. 
