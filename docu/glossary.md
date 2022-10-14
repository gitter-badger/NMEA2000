
\page pgGloss Glossary
\tableofcontents


# Purpose of NMEA 2000 instances
https://www.victronenergy.com/upload/documents/Technical-Information-Data-communication-with-Victron-Energy-products_EN.pdf
https://www.victronenergy.com/live/ve.can:changing_nmea2000_instances
Instances are used in an NMEA 2000 network to identify multiple similar products connected on the same network.

As an example, take a system with two battery monitors (one for the main battery bank, and another for the hydraulic-thruster bank) and also a Quattro inverter/charger. All three of those devices will send their battery voltage measurements out on the N2K network. For the displays to show these values at the right place, they need to know which voltage belongs to what battery. That is what instances are for.
1.2 Different types of instances

There various types of instances, and for marine systems are two that matter: the Device instance and the Data instance. Details and differences of each type are explained in detail in the Cerbo GX manual, NMEA 2000 chapter.

WARNING: whilst it is possible to change the data instances, changing them on a Victron devices will render that device impossible to read correctly by other Victron devices. For example, changing the data instances on a Skylla-i will cause it to either not at all or not completely be visible on a GX device.
1.3 Recommend instancing setup for main MFD brands

Not all MFDs use instances the same. Some do not require setting up instances at all, others require to change the Device-instance and yet other brands require unique data instances or both.

Below documents explain the details for all major brands. Besides details on the required instancing; it also contains notes about supported, as well as non-supported, PGNs.

    NMEA 2000 configuration for Raymarine
    NMEA 2000 configuration for Garmin
    NMEA 2000 configuration for Furuno
    NMEA 2000 configuration for Navico (B&G, Simrad and Lowrance)

# Sequence ID

An upward counting number used to tie related information together between
different PGNs . For example, the SID would be used to tie together the COG,
SOG and RAIM values to a given position. 255=no valid position fix to tie it to.
Range 0 to 252 for valid position fixes
https://www.nmea.org/Assets/20170204%20nmea%202000%20leeway%20pgn%20final.pdf

SID – The sequence identifier field is used to tie related PGNs together. For example, the GPS200 will transmit identical SIDs for 126992 (System Time), 128259 (Speed), 129026 (COG and SOG, Rapid Update), 129029 (GNSS Position Data), 129539 (GNSS DOPs), and 129540 (GNSS Satellites in View) to indicate that the readings are linked together (i.e., the data from each PGN was taken at the same time although they are reported at slightly different times).