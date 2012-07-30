# Openflights.org Data: Airlines, Airports and Routes

> The following documentation is adapted from the
[OpenFlights documentation](http://openflights.org/data.html); see their licensing statement below.

Original:

* [Airport Info](http://openflights.org/data.html#airport)
* [Airline Info](http://openflights.org/data.html#airline)
* [Airflight Routes](http://openflights.org/data.html#route)

### Encoding

The data is ISO 8859-1 (Latin-1) encoded, with no special characters.

### Time zones

OpenFlights uses UTC offsets as time zones, so UTC+8 (Singapore) is recorded
as "+8" and UTC-5 (New York) as "-5". Time zone data for OpenFlights was
obtained from EarthTools.

### Daylight Savings Time (DST)

When active, Daylight Savings Time (DST), or "summer time", adds one to the normal timezone, so
eg. New York, normally UTC-5, becomes UTC-4 while DST is active. OpenFlights currently understands
the following types of DST:

* European       -- Starts on the last Sunday of March, ends on the last Sunday of October. Used in all European countries (except Iceland), as well as Greenland, Lebanon, Russia and Tunisia. Jordan and Syria are almost the same, starting and ending on Friday instead of Sunday. European DST is also used to (crudely) approximate Iranian DST, although they actually use an entirely different calendar.
* US/Canada      -- Starts on the second Sunday of March, ends on the first Sunday of November. Used in the United States (except Arizona, Hawaii and island territories) and Canada (with convoluted exceptions).
* South American -- Starts on the third Sunday of October, ends on the third Sunday of March. Used, with some variance in the exact dates, in Argentina, Chile, Mexico, Paraguay, Uruguay as well as the African states of Namibia and Mauritius.
* Australia      -- Starts on the first Sunday of October, ends on the first Sunday of April. Not used in Queensland and the Northern Territory.
* New Zealand    -- Starts on the last Sunday of September, ends on the first Sunday of April.
* None           -- DST not observed.
* Unknown        -- DST status not known. The same as "None".

The rules for DST change constantly and not all airports are up to date or marked correctly. Please contact the OpenFlights team if you find any errors.

Examples

* A flight in April departs Singapore (SIN) at 20:00 and arrives in Chennai (MAA) at 21:30. Singapore is UTC+8, Chennai is UTC+5.5. Flight duration is thus (21:30-20:00) - (05:30-08:00) = 1:30 - (-2:30) = 4:00.
* A flight in June departs Newark (EWR) at 23:00 and arrives in Singapore (SIN) at 07:40 + 2 days. Singapore is UTC+8, New York is UTC-4 (DST). Flight duration is thus (07:40+48:00)-23:00 - (-04:00-08:00) = -32:40 - -(12:00) = 20:40.

### OpenFlights License and Disclaimer

The OpenFlights Airport, Airline and Route Databases are made available under the Open Database License. Any rights in individual contents of the database are licensed under the Database Contents License.

Airport data derived from OurAirports and DAFIF, as well as route data from Airline Route Mapper, is in the public domain. Airline data derived from Wikipedia may be subject to the GNU Free Documentation License. Whether these databases pass the threshold of originality and are thus copyrightable in the United States is an open question, and Contentshare does not assert the validity or lack thereof of such a claim.

This data is not suitable for navigation. OpenFlights does not assume any responsibility whatsoever for its accuracy, and consequently assumes no liability whatsoever for results obtained or loss or damage incurred as a result of application of the data. OpenFlights expressly disclaims all warranties, expressed or implied, including but not limited to implied warranties of merchantability and fitness for any particular purpose.

Any corrections will be gratefully received.


### Repairs

* 2609: fixed name, to Plácido
* 6829: Bogus ICAO for Orchid Beach (was KOKB)
* 6826: Bogus ICAO for Bamburi (was KBMQ)
* 6449: Has no ICAO (remove KBVU) for Boulder City Municipal Airport.  
* 6457: Has no ICAO (removed KW55) for Kenmore Air Harbor Seaplane Base
* 6459: Bougs ICAO/IATA for Magas (Nazran, Russia) (was "%u0","%u04")
* 7013: IATA was GBN, should be GBD (Great Bend Municipal)
* 7086: ICAO was KNOP, should be KONP
* 7767: IDL and KIDL are the FAA/ICAO for Indianola Municipal Airport; it has no IATA. Removed KIDL from Idlewild Intl, made clear it's (Now JFK); left its IATA field.
* 7784, 7792, 7802, 8071: A bunch of railroads with Bogus ICAO and IATA
* 7994: Bogus ICAO KIEV
* 8030: Longitude off by - sign for Deer Valley Municipal Airport
* 8192: Bogus IATA ЛНЙ for Krainiy Baikonur, Kazakhstan
* 8274: IATA was FRP, should be FPR for St Lucie County International 
* 8275: bogus ICAO -- ALX_

In case you're wondering, the ICAO is not *always* the FAA plus a 'K' : the (missing Beluga airport) has iata BVU / icao PABG / faa BLG. Note the near-conflict between Beluga (BVU/PABG/BLG) with Boulder City Municipal Airport (BLD/KBVU/BVU) -- Beluga's IATA is Boulder's FAA, and Beluga's ICAO doesn't match its FAA.


        iata	icao	faa
        BVU	PABG	BLG	IATA: BVU, ICAO: PABG, FAA LID: BLG
        UTM	KUTA	UTA	IATA: UTM, ICAO: KUTA, FAA LID: UTA, formerly M97
        RKH	KUZA	UZA	IATA: RKH, ICAO: KUZA, FAA LID: UZA
        LKE		W55	IATA: LKE,             FAA LID: W55
        UST	KSGJ	SGJ	IATA: UST, ICAO: KSGJ, FAA LID: SGJ
	BLD	KBVU	BVU	IATA: BLD, ICAO: KBVU, FAA LID: BVU

	ruby -ne 'puts $_ unless $_ =~ /^[\-\~A-Z0-9]{1,3}\t[A-Z]{4}\t([A-Z]*)\t([^\t]+)(?:\t([^\t]*))?/'

