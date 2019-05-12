# Database schemas

## Table definition
* Place columns of the same type close to each other - better for the physical storage
* Normalization at first when there are no concrete business requirements. Use denormalization only for the requests optimization
* Create a SCHEMA, do not use default one (public)
* Use TABLESPACE for the database with the different purpose - for example, for archive database
