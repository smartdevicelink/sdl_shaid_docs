# Read Countries
#### Requires admin privileges
Retrieve a list of supported countries an Application can choose to be associated with. An Application may be associated with many countries.

## HTTP Request
`GET` https://shaid.smartdevicelink.com/api/v1/country

## Query Parameters
| Parameter | Required | Default | Description |
|-----------|----------|---------|-------------|
| `application_uuid` | No | | Check each Country against the given Application to see if it is currently chosen by the Application, returned by the `is_selected` attribute. |

## Example Response

```json
{
  "meta": {
    "request_id": "839991d1-eaaf-4846-9993-17497cf8bba8",
    "code": 200,
    "message": "Success!"
  },
  "data": {
    "countries": [
      {
        "id": 3,
        "iso": "AF",
        "name": "Afghanistan",
        "is_selected": false
      },
      {
        "id": 6,
        "iso": "AL",
        "name": "Albania",
        "is_selected": false
      },
      {
        "id": 62,
        "iso": "DZ",
        "name": "Algeria",
        "is_selected": false
      },
      {
        "id": 11,
        "iso": "AS",
        "name": "American Samoa",
        "is_selected": false
      },
      {
        "id": 1,
        "iso": "AD",
        "name": "Andorra",
        "is_selected": false
      },
      {
        "id": 8,
        "iso": "AO",
        "name": "Angola",
        "is_selected": false
      },
      {
        "id": 5,
        "iso": "AI",
        "name": "Anguilla",
        "is_selected": false
      },
      {
        "id": 9,
        "iso": "AQ",
        "name": "Antarctica",
        "is_selected": false
      },
      {
        "id": 4,
        "iso": "AG",
        "name": "Antigua and Barbuda",
        "is_selected": false
      },
      {
        "id": 10,
        "iso": "AR",
        "name": "Argentina",
        "is_selected": false
      },
      {
        "id": 7,
        "iso": "AM",
        "name": "Armenia",
        "is_selected": false
      },
      {
        "id": 14,
        "iso": "AW",
        "name": "Aruba",
        "is_selected": false
      },
      {
        "id": 13,
        "iso": "AU",
        "name": "Australia",
        "is_selected": false
      },
      {
        "id": 12,
        "iso": "AT",
        "name": "Austria",
        "is_selected": false
      },
      {
        "id": 16,
        "iso": "AZ",
        "name": "Azerbaijan",
        "is_selected": false
      },
      {
        "id": 32,
        "iso": "BS",
        "name": "Bahamas",
        "is_selected": false
      },
      {
        "id": 23,
        "iso": "BH",
        "name": "Bahrain",
        "is_selected": false
      },
      {
        "id": 19,
        "iso": "BD",
        "name": "Bangladesh",
        "is_selected": false
      },
      {
        "id": 18,
        "iso": "BB",
        "name": "Barbados",
        "is_selected": false
      },
      {
        "id": 36,
        "iso": "BY",
        "name": "Belarus",
        "is_selected": false
      },
      {
        "id": 20,
        "iso": "BE",
        "name": "Belgium",
        "is_selected": false
      },
      {
        "id": 37,
        "iso": "BZ",
        "name": "Belize",
        "is_selected": false
      },
      {
        "id": 25,
        "iso": "BJ",
        "name": "Benin",
        "is_selected": false
      },
      {
        "id": 27,
        "iso": "BM",
        "name": "Bermuda",
        "is_selected": false
      },
      {
        "id": 33,
        "iso": "BT",
        "name": "Bhutan",
        "is_selected": false
      },
      {
        "id": 29,
        "iso": "BO",
        "name": "Bolivia",
        "is_selected": false
      },
      {
        "id": 17,
        "iso": "BA",
        "name": "Bosnia and Herzegovina",
        "is_selected": false
      },
      {
        "id": 35,
        "iso": "BW",
        "name": "Botswana",
        "is_selected": false
      },
      {
        "id": 34,
        "iso": "BV",
        "name": "Bouvet Island",
        "is_selected": false
      },
      {
        "id": 31,
        "iso": "BR",
        "name": "Brazil",
        "is_selected": false
      },
      {
        "id": 106,
        "iso": "IO",
        "name": "British Indian Ocean Territory",
        "is_selected": false
      },
      {
        "id": 28,
        "iso": "BN",
        "name": "Brunei Darussalam",
        "is_selected": false
      },
      {
        "id": 22,
        "iso": "BG",
        "name": "Bulgaria",
        "is_selected": false
      },
      {
        "id": 21,
        "iso": "BF",
        "name": "Burkina Faso",
        "is_selected": false
      },
      {
        "id": 24,
        "iso": "BI",
        "name": "Burundi",
        "is_selected": false
      },
      {
        "id": 117,
        "iso": "KH",
        "name": "Cambodia",
        "is_selected": false
      },
      {
        "id": 47,
        "iso": "CM",
        "name": "Cameroon",
        "is_selected": false
      },
      {
        "id": 38,
        "iso": "CA",
        "name": "Canada",
        "is_selected": false
      },
      {
        "id": 52,
        "iso": "CV",
        "name": "Cape Verde",
        "is_selected": false
      },
      {
        "id": 30,
        "iso": "BQ",
        "name": "Caribbean Netherlands ",
        "is_selected": false
      },
      {
        "id": 124,
        "iso": "KY",
        "name": "Cayman Islands",
        "is_selected": false
      },
      {
        "id": 41,
        "iso": "CF",
        "name": "Central African Republic",
        "is_selected": false
      },
      {
        "id": 215,
        "iso": "TD",
        "name": "Chad",
        "is_selected": false
      },
      {
        "id": 46,
        "iso": "CL",
        "name": "Chile",
        "is_selected": false
      },
      {
        "id": 48,
        "iso": "CN",
        "name": "China",
        "is_selected": false
      },
      {
        "id": 54,
        "iso": "CX",
        "name": "Christmas Island",
        "is_selected": false
      },
      {
        "id": 39,
        "iso": "CC",
        "name": "Cocos (Keeling) Islands",
        "is_selected": false
      },
      {
        "id": 49,
        "iso": "CO",
        "name": "Colombia",
        "is_selected": false
      },
      {
        "id": 119,
        "iso": "KM",
        "name": "Comoros",
        "is_selected": false
      },
      {
        "id": 42,
        "iso": "CG",
        "name": "Congo",
        "is_selected": false
      },
      {
        "id": 40,
        "iso": "CD",
        "name": "Congo, Democratic Republic of",
        "is_selected": false
      },
      {
        "id": 45,
        "iso": "CK",
        "name": "Cook Islands",
        "is_selected": false
      },
      {
        "id": 50,
        "iso": "CR",
        "name": "Costa Rica",
        "is_selected": false
      },
      {
        "id": 98,
        "iso": "HR",
        "name": "Croatia",
        "is_selected": false
      },
      {
        "id": 51,
        "iso": "CU",
        "name": "Cuba",
        "is_selected": false
      },
      {
        "id": 53,
        "iso": "CW",
        "name": "Curaçao",
        "is_selected": false
      },
      {
        "id": 55,
        "iso": "CY",
        "name": "Cyprus",
        "is_selected": false
      },
      {
        "id": 56,
        "iso": "CZ",
        "name": "Czech Republic",
        "is_selected": false
      },
      {
        "id": 44,
        "iso": "CI",
        "name": "Côte d'Ivoire",
        "is_selected": false
      },
      {
        "id": 59,
        "iso": "DK",
        "name": "Denmark",
        "is_selected": false
      },
      {
        "id": 58,
        "iso": "DJ",
        "name": "Djibouti",
        "is_selected": false
      },
      {
        "id": 60,
        "iso": "DM",
        "name": "Dominica",
        "is_selected": false
      },
      {
        "id": 61,
        "iso": "DO",
        "name": "Dominican Republic",
        "is_selected": false
      },
      {
        "id": 63,
        "iso": "EC",
        "name": "Ecuador",
        "is_selected": false
      },
      {
        "id": 65,
        "iso": "EG",
        "name": "Egypt",
        "is_selected": false
      },
      {
        "id": 210,
        "iso": "SV",
        "name": "El Salvador",
        "is_selected": false
      },
      {
        "id": 88,
        "iso": "GQ",
        "name": "Equatorial Guinea",
        "is_selected": false
      },
      {
        "id": 67,
        "iso": "ER",
        "name": "Eritrea",
        "is_selected": false
      },
      {
        "id": 64,
        "iso": "EE",
        "name": "Estonia",
        "is_selected": false
      },
      {
        "id": 69,
        "iso": "ET",
        "name": "Ethiopia",
        "is_selected": false
      },
      {
        "id": 72,
        "iso": "FK",
        "name": "Falkland Islands",
        "is_selected": false
      },
      {
        "id": 74,
        "iso": "FO",
        "name": "Faroe Islands",
        "is_selected": false
      },
      {
        "id": 71,
        "iso": "FJ",
        "name": "Fiji",
        "is_selected": false
      },
      {
        "id": 70,
        "iso": "FI",
        "name": "Finland",
        "is_selected": false
      },
      {
        "id": 75,
        "iso": "FR",
        "name": "France",
        "is_selected": false
      },
      {
        "id": 80,
        "iso": "GF",
        "name": "French Guiana",
        "is_selected": false
      },
      {
        "id": 175,
        "iso": "PF",
        "name": "French Polynesia",
        "is_selected": false
      },
      {
        "id": 216,
        "iso": "TF",
        "name": "French Southern Territories",
        "is_selected": false
      },
      {
        "id": 76,
        "iso": "GA",
        "name": "Gabon",
        "is_selected": false
      },
      {
        "id": 85,
        "iso": "GM",
        "name": "Gambia",
        "is_selected": false
      },
      {
        "id": 79,
        "iso": "GE",
        "name": "Georgia",
        "is_selected": false
      },
      {
        "id": 57,
        "iso": "DE",
        "name": "Germany",
        "is_selected": false
      },
      {
        "id": 82,
        "iso": "GH",
        "name": "Ghana",
        "is_selected": false
      },
      {
        "id": 83,
        "iso": "GI",
        "name": "Gibraltar",
        "is_selected": false
      },
      {
        "id": 89,
        "iso": "GR",
        "name": "Greece",
        "is_selected": false
      },
      {
        "id": 84,
        "iso": "GL",
        "name": "Greenland",
        "is_selected": false
      },
      {
        "id": 78,
        "iso": "GD",
        "name": "Grenada",
        "is_selected": false
      },
      {
        "id": 87,
        "iso": "GP",
        "name": "Guadeloupe",
        "is_selected": false
      },
      {
        "id": 92,
        "iso": "GU",
        "name": "Guam",
        "is_selected": false
      },
      {
        "id": 91,
        "iso": "GT",
        "name": "Guatemala",
        "is_selected": false
      },
      {
        "id": 81,
        "iso": "GG",
        "name": "Guernsey",
        "is_selected": false
      },
      {
        "id": 86,
        "iso": "GN",
        "name": "Guinea",
        "is_selected": false
      },
      {
        "id": 93,
        "iso": "GW",
        "name": "Guinea-Bissau",
        "is_selected": false
      },
      {
        "id": 94,
        "iso": "GY",
        "name": "Guyana",
        "is_selected": false
      },
      {
        "id": 99,
        "iso": "HT",
        "name": "Haiti",
        "is_selected": false
      },
      {
        "id": 96,
        "iso": "HM",
        "name": "Heard and McDonald Islands",
        "is_selected": false
      },
      {
        "id": 97,
        "iso": "HN",
        "name": "Honduras",
        "is_selected": false
      },
      {
        "id": 95,
        "iso": "HK",
        "name": "Hong Kong",
        "is_selected": false
      },
      {
        "id": 100,
        "iso": "HU",
        "name": "Hungary",
        "is_selected": false
      },
      {
        "id": 109,
        "iso": "IS",
        "name": "Iceland",
        "is_selected": false
      },
      {
        "id": 105,
        "iso": "IN",
        "name": "India",
        "is_selected": false
      },
      {
        "id": 101,
        "iso": "ID",
        "name": "Indonesia",
        "is_selected": false
      },
      {
        "id": 108,
        "iso": "IR",
        "name": "Iran",
        "is_selected": false
      },
      {
        "id": 107,
        "iso": "IQ",
        "name": "Iraq",
        "is_selected": false
      },
      {
        "id": 102,
        "iso": "IE",
        "name": "Ireland",
        "is_selected": false
      },
      {
        "id": 104,
        "iso": "IM",
        "name": "Isle of Man",
        "is_selected": false
      },
      {
        "id": 103,
        "iso": "IL",
        "name": "Israel",
        "is_selected": false
      },
      {
        "id": 110,
        "iso": "IT",
        "name": "Italy",
        "is_selected": false
      },
      {
        "id": 112,
        "iso": "JM",
        "name": "Jamaica",
        "is_selected": false
      },
      {
        "id": 114,
        "iso": "JP",
        "name": "Japan",
        "is_selected": false
      },
      {
        "id": 111,
        "iso": "JE",
        "name": "Jersey",
        "is_selected": false
      },
      {
        "id": 113,
        "iso": "JO",
        "name": "Jordan",
        "is_selected": false
      },
      {
        "id": 125,
        "iso": "KZ",
        "name": "Kazakhstan",
        "is_selected": false
      },
      {
        "id": 115,
        "iso": "KE",
        "name": "Kenya",
        "is_selected": false
      },
      {
        "id": 118,
        "iso": "KI",
        "name": "Kiribati",
        "is_selected": false
      },
      {
        "id": 123,
        "iso": "KW",
        "name": "Kuwait",
        "is_selected": false
      },
      {
        "id": 116,
        "iso": "KG",
        "name": "Kyrgyzstan",
        "is_selected": false
      },
      {
        "id": 126,
        "iso": "LA",
        "name": "Lao People's Democratic Republic",
        "is_selected": false
      },
      {
        "id": 135,
        "iso": "LV",
        "name": "Latvia",
        "is_selected": false
      },
      {
        "id": 127,
        "iso": "LB",
        "name": "Lebanon",
        "is_selected": false
      },
      {
        "id": 132,
        "iso": "LS",
        "name": "Lesotho",
        "is_selected": false
      },
      {
        "id": 131,
        "iso": "LR",
        "name": "Liberia",
        "is_selected": false
      },
      {
        "id": 136,
        "iso": "LY",
        "name": "Libya",
        "is_selected": false
      },
      {
        "id": 129,
        "iso": "LI",
        "name": "Liechtenstein",
        "is_selected": false
      },
      {
        "id": 133,
        "iso": "LT",
        "name": "Lithuania",
        "is_selected": false
      },
      {
        "id": 134,
        "iso": "LU",
        "name": "Luxembourg",
        "is_selected": false
      },
      {
        "id": 148,
        "iso": "MO",
        "name": "Macau",
        "is_selected": false
      },
      {
        "id": 144,
        "iso": "MK",
        "name": "Macedonia",
        "is_selected": false
      },
      {
        "id": 142,
        "iso": "MG",
        "name": "Madagascar",
        "is_selected": false
      },
      {
        "id": 156,
        "iso": "MW",
        "name": "Malawi",
        "is_selected": false
      },
      {
        "id": 158,
        "iso": "MY",
        "name": "Malaysia",
        "is_selected": false
      },
      {
        "id": 155,
        "iso": "MV",
        "name": "Maldives",
        "is_selected": false
      },
      {
        "id": 145,
        "iso": "ML",
        "name": "Mali",
        "is_selected": false
      },
      {
        "id": 153,
        "iso": "MT",
        "name": "Malta",
        "is_selected": false
      },
      {
        "id": 143,
        "iso": "MH",
        "name": "Marshall Islands",
        "is_selected": false
      },
      {
        "id": 150,
        "iso": "MQ",
        "name": "Martinique",
        "is_selected": false
      },
      {
        "id": 151,
        "iso": "MR",
        "name": "Mauritania",
        "is_selected": false
      },
      {
        "id": 154,
        "iso": "MU",
        "name": "Mauritius",
        "is_selected": false
      },
      {
        "id": 246,
        "iso": "YT",
        "name": "Mayotte",
        "is_selected": false
      },
      {
        "id": 157,
        "iso": "MX",
        "name": "Mexico",
        "is_selected": false
      },
      {
        "id": 73,
        "iso": "FM",
        "name": "Micronesia, Federated States of",
        "is_selected": false
      },
      {
        "id": 139,
        "iso": "MD",
        "name": "Moldova",
        "is_selected": false
      },
      {
        "id": 138,
        "iso": "MC",
        "name": "Monaco",
        "is_selected": false
      },
      {
        "id": 147,
        "iso": "MN",
        "name": "Mongolia",
        "is_selected": false
      },
      {
        "id": 140,
        "iso": "ME",
        "name": "Montenegro",
        "is_selected": false
      },
      {
        "id": 152,
        "iso": "MS",
        "name": "Montserrat",
        "is_selected": false
      },
      {
        "id": 137,
        "iso": "MA",
        "name": "Morocco",
        "is_selected": false
      },
      {
        "id": 159,
        "iso": "MZ",
        "name": "Mozambique",
        "is_selected": false
      },
      {
        "id": 146,
        "iso": "MM",
        "name": "Myanmar",
        "is_selected": false
      },
      {
        "id": 160,
        "iso": "NA",
        "name": "Namibia",
        "is_selected": false
      },
      {
        "id": 169,
        "iso": "NR",
        "name": "Nauru",
        "is_selected": false
      },
      {
        "id": 168,
        "iso": "NP",
        "name": "Nepal",
        "is_selected": false
      },
      {
        "id": 161,
        "iso": "NC",
        "name": "New Caledonia",
        "is_selected": false
      },
      {
        "id": 171,
        "iso": "NZ",
        "name": "New Zealand",
        "is_selected": false
      },
      {
        "id": 165,
        "iso": "NI",
        "name": "Nicaragua",
        "is_selected": false
      },
      {
        "id": 162,
        "iso": "NE",
        "name": "Niger",
        "is_selected": false
      },
      {
        "id": 164,
        "iso": "NG",
        "name": "Nigeria",
        "is_selected": false
      },
      {
        "id": 170,
        "iso": "NU",
        "name": "Niue",
        "is_selected": false
      },
      {
        "id": 163,
        "iso": "NF",
        "name": "Norfolk Island",
        "is_selected": false
      },
      {
        "id": 121,
        "iso": "KP",
        "name": "North Korea",
        "is_selected": false
      },
      {
        "id": 149,
        "iso": "MP",
        "name": "Northern Mariana Islands",
        "is_selected": false
      },
      {
        "id": 167,
        "iso": "NO",
        "name": "Norway",
        "is_selected": false
      },
      {
        "id": 172,
        "iso": "OM",
        "name": "Oman",
        "is_selected": false
      },
      {
        "id": 178,
        "iso": "PK",
        "name": "Pakistan",
        "is_selected": false
      },
      {
        "id": 185,
        "iso": "PW",
        "name": "Palau",
        "is_selected": false
      },
      {
        "id": 183,
        "iso": "PS",
        "name": "Palestine, State of",
        "is_selected": false
      },
      {
        "id": 173,
        "iso": "PA",
        "name": "Panama",
        "is_selected": false
      },
      {
        "id": 176,
        "iso": "PG",
        "name": "Papua New Guinea",
        "is_selected": false
      },
      {
        "id": 186,
        "iso": "PY",
        "name": "Paraguay",
        "is_selected": false
      },
      {
        "id": 174,
        "iso": "PE",
        "name": "Peru",
        "is_selected": false
      },
      {
        "id": 177,
        "iso": "PH",
        "name": "Philippines",
        "is_selected": false
      },
      {
        "id": 181,
        "iso": "PN",
        "name": "Pitcairn",
        "is_selected": false
      },
      {
        "id": 179,
        "iso": "PL",
        "name": "Poland",
        "is_selected": false
      },
      {
        "id": 184,
        "iso": "PT",
        "name": "Portugal",
        "is_selected": false
      },
      {
        "id": 182,
        "iso": "PR",
        "name": "Puerto Rico",
        "is_selected": false
      },
      {
        "id": 187,
        "iso": "QA",
        "name": "Qatar",
        "is_selected": false
      },
      {
        "id": 189,
        "iso": "RO",
        "name": "Romania",
        "is_selected": false
      },
      {
        "id": 191,
        "iso": "RU",
        "name": "Russian Federation",
        "is_selected": false
      },
      {
        "id": 192,
        "iso": "RW",
        "name": "Rwanda",
        "is_selected": false
      },
      {
        "id": 188,
        "iso": "RE",
        "name": "Réunion",
        "is_selected": false
      },
      {
        "id": 26,
        "iso": "BL",
        "name": "Saint Barthélemy",
        "is_selected": false
      },
      {
        "id": 199,
        "iso": "SH",
        "name": "Saint Helena",
        "is_selected": false
      },
      {
        "id": 120,
        "iso": "KN",
        "name": "Saint Kitts and Nevis",
        "is_selected": false
      },
      {
        "id": 128,
        "iso": "LC",
        "name": "Saint Lucia",
        "is_selected": false
      },
      {
        "id": 237,
        "iso": "VC",
        "name": "Saint Vincent and the Grenadines",
        "is_selected": false
      },
      {
        "id": 141,
        "iso": "MF",
        "name": "Saint-Martin (France)",
        "is_selected": false
      },
      {
        "id": 244,
        "iso": "WS",
        "name": "Samoa",
        "is_selected": false
      },
      {
        "id": 204,
        "iso": "SM",
        "name": "San Marino",
        "is_selected": false
      },
      {
        "id": 209,
        "iso": "ST",
        "name": "Sao Tome and Principe",
        "is_selected": false
      },
      {
        "id": 193,
        "iso": "SA",
        "name": "Saudi Arabia",
        "is_selected": false
      },
      {
        "id": 205,
        "iso": "SN",
        "name": "Senegal",
        "is_selected": false
      },
      {
        "id": 190,
        "iso": "RS",
        "name": "Serbia",
        "is_selected": false
      },
      {
        "id": 195,
        "iso": "SC",
        "name": "Seychelles",
        "is_selected": false
      },
      {
        "id": 203,
        "iso": "SL",
        "name": "Sierra Leone",
        "is_selected": false
      },
      {
        "id": 198,
        "iso": "SG",
        "name": "Singapore",
        "is_selected": false
      },
      {
        "id": 211,
        "iso": "SX",
        "name": "Sint Maarten (Dutch part)",
        "is_selected": false
      },
      {
        "id": 202,
        "iso": "SK",
        "name": "Slovakia",
        "is_selected": false
      },
      {
        "id": 200,
        "iso": "SI",
        "name": "Slovenia",
        "is_selected": false
      },
      {
        "id": 194,
        "iso": "SB",
        "name": "Solomon Islands",
        "is_selected": false
      },
      {
        "id": 206,
        "iso": "SO",
        "name": "Somalia",
        "is_selected": false
      },
      {
        "id": 247,
        "iso": "ZA",
        "name": "South Africa",
        "is_selected": false
      },
      {
        "id": 90,
        "iso": "GS",
        "name": "South Georgia and the South Sandwich Islands",
        "is_selected": false
      },
      {
        "id": 122,
        "iso": "KR",
        "name": "South Korea",
        "is_selected": false
      },
      {
        "id": 208,
        "iso": "SS",
        "name": "South Sudan",
        "is_selected": false
      },
      {
        "id": 68,
        "iso": "ES",
        "name": "Spain",
        "is_selected": false
      },
      {
        "id": 130,
        "iso": "LK",
        "name": "Sri Lanka",
        "is_selected": false
      },
      {
        "id": 180,
        "iso": "PM",
        "name": "St. Pierre and Miquelon",
        "is_selected": false
      },
      {
        "id": 196,
        "iso": "SD",
        "name": "Sudan",
        "is_selected": false
      },
      {
        "id": 207,
        "iso": "SR",
        "name": "Suriname",
        "is_selected": false
      },
      {
        "id": 201,
        "iso": "SJ",
        "name": "Svalbard and Jan Mayen Islands",
        "is_selected": false
      },
      {
        "id": 213,
        "iso": "SZ",
        "name": "Swaziland",
        "is_selected": false
      },
      {
        "id": 197,
        "iso": "SE",
        "name": "Sweden",
        "is_selected": false
      },
      {
        "id": 43,
        "iso": "CH",
        "name": "Switzerland",
        "is_selected": false
      },
      {
        "id": 212,
        "iso": "SY",
        "name": "Syria",
        "is_selected": false
      },
      {
        "id": 228,
        "iso": "TW",
        "name": "Taiwan",
        "is_selected": false
      },
      {
        "id": 219,
        "iso": "TJ",
        "name": "Tajikistan",
        "is_selected": false
      },
      {
        "id": 229,
        "iso": "TZ",
        "name": "Tanzania",
        "is_selected": false
      },
      {
        "id": 218,
        "iso": "TH",
        "name": "Thailand",
        "is_selected": false
      },
      {
        "id": 166,
        "iso": "NL",
        "name": "The Netherlands",
        "is_selected": false
      },
      {
        "id": 221,
        "iso": "TL",
        "name": "Timor-Leste",
        "is_selected": false
      },
      {
        "id": 217,
        "iso": "TG",
        "name": "Togo",
        "is_selected": false
      },
      {
        "id": 220,
        "iso": "TK",
        "name": "Tokelau",
        "is_selected": false
      },
      {
        "id": 224,
        "iso": "TO",
        "name": "Tonga",
        "is_selected": false
      },
      {
        "id": 226,
        "iso": "TT",
        "name": "Trinidad and Tobago",
        "is_selected": false
      },
      {
        "id": 223,
        "iso": "TN",
        "name": "Tunisia",
        "is_selected": false
      },
      {
        "id": 225,
        "iso": "TR",
        "name": "Turkey",
        "is_selected": false
      },
      {
        "id": 222,
        "iso": "TM",
        "name": "Turkmenistan",
        "is_selected": false
      },
      {
        "id": 214,
        "iso": "TC",
        "name": "Turks and Caicos Islands",
        "is_selected": false
      },
      {
        "id": 227,
        "iso": "TV",
        "name": "Tuvalu",
        "is_selected": false
      },
      {
        "id": 231,
        "iso": "UG",
        "name": "Uganda",
        "is_selected": false
      },
      {
        "id": 230,
        "iso": "UA",
        "name": "Ukraine",
        "is_selected": false
      },
      {
        "id": 2,
        "iso": "AE",
        "name": "United Arab Emirates",
        "is_selected": false
      },
      {
        "id": 77,
        "iso": "GB",
        "name": "United Kingdom",
        "is_selected": false
      },
      {
        "id": 233,
        "iso": "US",
        "name": "United States",
        "is_selected": true
      },
      {
        "id": 232,
        "iso": "UM",
        "name": "United States Minor Outlying Islands",
        "is_selected": false
      },
      {
        "id": 234,
        "iso": "UY",
        "name": "Uruguay",
        "is_selected": false
      },
      {
        "id": 235,
        "iso": "UZ",
        "name": "Uzbekistan",
        "is_selected": false
      },
      {
        "id": 242,
        "iso": "VU",
        "name": "Vanuatu",
        "is_selected": false
      },
      {
        "id": 236,
        "iso": "VA",
        "name": "Vatican",
        "is_selected": false
      },
      {
        "id": 238,
        "iso": "VE",
        "name": "Venezuela",
        "is_selected": false
      },
      {
        "id": 241,
        "iso": "VN",
        "name": "Vietnam",
        "is_selected": false
      },
      {
        "id": 239,
        "iso": "VG",
        "name": "Virgin Islands (British)",
        "is_selected": false
      },
      {
        "id": 240,
        "iso": "VI",
        "name": "Virgin Islands (U.S.)",
        "is_selected": false
      },
      {
        "id": 243,
        "iso": "WF",
        "name": "Wallis and Futuna Islands",
        "is_selected": false
      },
      {
        "id": 66,
        "iso": "EH",
        "name": "Western Sahara",
        "is_selected": false
      },
      {
        "id": 245,
        "iso": "YE",
        "name": "Yemen",
        "is_selected": false
      },
      {
        "id": 248,
        "iso": "ZM",
        "name": "Zambia",
        "is_selected": false
      },
      {
        "id": 249,
        "iso": "ZW",
        "name": "Zimbabwe",
        "is_selected": false
      },
      {
        "id": 15,
        "iso": "AX",
        "name": "Åland Islands",
        "is_selected": false
      }
    ]
  }
}
```
