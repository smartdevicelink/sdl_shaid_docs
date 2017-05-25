# Read Permissions
#### Requires admin privileges
Retrieve a list of supported permissions an Application can request access to. An Application can use many permissions.

## HTTP Request
`GET` https://shaid.smartdevicelink.com/api/v1/permission

## Query Parameters
| Parameter | Required | Default | Description |
|-----------|----------|---------|-------------|
| `application_uuid` | No | | Check each Permission against the given Application to see if it is currently in use by the Application, returned by the `selected_hmi_level` attribute. |

## Example Response

```json
{
  "meta": {
    "request_id": "6eaa4407-f8bf-4b7f-b001-b6ceaeb2102d",
    "code": 200,
    "message": "Success!"
  },
  "data": {
    "permission_categories": [
      {
        "id": 4,
        "name": "Driving",
        "description": null,
        "permissions": [
          {
            "id": 18,
            "key": "accPedalPosition",
            "name": "Accelerator Pedal Position",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 20,
            "key": "driverBraking",
            "name": "Braking",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 21,
            "key": "myKey",
            "name": "My Key",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 23,
            "key": "rpm",
            "name": "RPMs",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 19,
            "key": "beltStatus",
            "name": "Seatbelt Status",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 24,
            "key": "steeringWheelAngle",
            "name": "Steering Wheel Angle",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 22,
            "key": "prndl",
            "name": "Transmission Gear (PRNDL)",
            "selected_hmi_level": "HMI_NONE"
          }
        ]
      },
      {
        "id": 5,
        "name": "Emergency",
        "description": null,
        "permissions": [
          {
            "id": 25,
            "key": "airbagStatus",
            "name": "Airbag Status",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 26,
            "key": "clusterModeStatus",
            "name": "Cluster Mode Status",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 27,
            "key": "eCallInfo",
            "name": "Emergency Call Information",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 28,
            "key": "emergencyEvent",
            "name": "Emergency Event",
            "selected_hmi_level": "HMI_NONE"
          }
        ]
      },
      {
        "id": 1,
        "name": "Location",
        "description": null,
        "permissions": [
          {
            "id": 1,
            "key": "gps",
            "name": "GPS",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 2,
            "key": "speed",
            "name": "Speed",
            "selected_hmi_level": "HMI_NONE"
          }
        ]
      },
      {
        "id": 2,
        "name": "Navigation",
        "description": null,
        "permissions": [
          {
            "id": 3,
            "key": "AlertManeuver",
            "name": "Alert Maneuver",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 4,
            "key": "ShowConstantTBT",
            "name": "Show Constant Turn-by-Turn",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 5,
            "key": "UpdateTurnList",
            "name": "Update the Turn List",
            "selected_hmi_level": "HMI_NONE"
          }
        ]
      },
      {
        "id": 6,
        "name": "Notification",
        "description": null,
        "permissions": [
        ]
      },
      {
        "id": 3,
        "name": "Vehicle",
        "description": null,
        "permissions": [
          {
            "id": 6,
            "key": "bodyInformation",
            "name": "Body Information",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 7,
            "key": "deviceStatus",
            "name": "Device Status",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 8,
            "key": "engineTorque",
            "name": "Engine Torque",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 9,
            "key": "externalTemperature",
            "name": "External Temperature",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 10,
            "key": "fuelLevel",
            "name": "Fuel Level",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 11,
            "key": "fuelLevel_State",
            "name": "Fuel Level State",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 12,
            "key": "headLampStatus",
            "name": "Headlamp Status",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 13,
            "key": "instantFuelConsumption",
            "name": "Instantaneous Fuel Consumption",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 14,
            "key": "odometer",
            "name": "Odometer",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 15,
            "key": "tirePressure",
            "name": "Tire Pressure",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 16,
            "key": "vin",
            "name": "Vehicle Identification Number (VIN)",
            "selected_hmi_level": "HMI_NONE"
          },
          {
            "id": 17,
            "key": "wiperStatus",
            "name": "Wiper Blade Status",
            "selected_hmi_level": "HMI_NONE"
          }
        ]
      }
    ]
  }
}
```
