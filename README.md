# Winmentor Data Import Exercise

This exercise is inspired by a real-case scenario and aims to evaluate your skills in manipulating, processing, and exporting data.

## Setup

This project is fully configured to run within Docker containers using Docker Compose, ensuring a seamless development environment across different machines. Below, you'll find instructions on how to get your environment up and running.

## Context
An accounting firm needs to convert certain files from Smartbill (an invoicing software) to the Winmentor format (an ERP) to import and finalize monthly financial statements. The goal of this exercise is to create a Laravel application that facilitates this process.

For a detailed overview of each service's configuration and how to customize it for your needs, refer to the docker-compose.yml file.

## Requirements

1. **CSV Data Import into MySQL**: Implement a solution to import data from the provided CSV files into a MySQL database. Ensure that none of the data is lost and that the database structure is suitable for storing this information.

2. **Client Management on Import**: With each import, new clients should be added, existing ones updated if necessary, and absent ones marked as deactivated (not deleted).

3. **Export Client Data in Winmentor Format**: Export the data of new clients into a .txt file compatible with Winmentor, following the structure below for each client. The file should contain only new clients, otherwise Winmentor will duplicate the existing ones. Provide only one file with all the new clients.

```ini
[ParteneriNoi_<CodFiscal>]
Denumire=
CodFiscal=
RegistruComert=
Localitate=
Judet=
Sediu=SEDIU SOCIAL
Tara=Romania
CodIntern=
Adresa=
Telefon=
Email=
PersoanaFizica=
Banci=
Conturi=
```

* In a single file add sections based on CodFiscal
* Populate as much of the fields you as can from the input CSV entries (clienti.csv)
* This file should **ONLY contain new customers**.

4. Export Invoice Data in Winmentor Format: Export the invoice data into a .txt file compatible with Winmentor, following the structure below:

```ini
[InfoPachet]
AnLucru=2024
LunaLucru=02
Tipdocument=FACTURA IESIRE

TotalFacturi=

[Factura_1]
NrDoc=
CasaDeMarcat=N
SerieCarnet=XXX
Data=dd.mm.yyyy
Scadenta=dd.mm.yyyy
Client=
CodClient=
Observatii=
TotalArticole=1
[Items_1]
Item_1=GENERAL;Lei;1;<Valoare Totala>;SEDIU

```

* The output file has one general section specifying the year, month and total number of invoices
* For each invoice have a new section with unique name for the import
* Replace/fill in as many fields as you can from the CSV entries
* All invoices are assumed to have a single item of quantity one. Replace <Valoare Totala> with total value from CSV

5. **Unit Tests**: Write unit tests for the implemented functionality.
6. **Documentation**: Add to this README file a section with instructions on how to run the application and any additional information you consider relevant.

You can choose to implement this exercise in any way you see fit (CLI, GUI), but the application should be able to run within the Docker environment provided.
