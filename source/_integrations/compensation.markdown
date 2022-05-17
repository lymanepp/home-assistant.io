---
title: Compensation
description: Instructions on how to integrate compensation sensors into Home Assistant.
ha_category:
  - Sensor
  - Utility
ha_iot_class: Calculated
ha_release: '2021.5'
ha_codeowners:
  - '@Petro31'
ha_domain: compensation
ha_platforms:
  - sensor
ha_integration_type: integration
---

The Compensation integration consumes the state from other sensors. It exports the compensated value as state and the following values as attributes: `entity_id` and `coefficients`.  A single polynomial, linear by default, is fit to all data points provided.

## Configuration

To enable the compensation sensor, add the following lines to your `configuration.yaml`:

```yaml
# Example configuration.yaml entry
compensation:
  media_player_db_volume:
    source: media_player.yamaha_receiver
    attribute: volume_level
    unit_of_measurement: dB
    hide_source: true
    data_points:
      - [0.2, -80.0]
      - [1.0, 0.0]
```

{% configuration %}
source:
  description: The entity to monitor/compensate.
  required: true
  type: string
data_points:
  description: "The collection of data point conversions with the format `[uncompensated_value, compensated_value]`.  e.g., `[1.0, 2.1]`. The number of required data points is equal to the polynomial `degree` + 1. For example, a linear compensation (with `degree: 1`) requires at least 2 data points."
  required: true
  type: list
unique_id:
  description: An ID that uniquely identifies this sensor. Set this to a unique value to allow customization through the UI.
  required: false
  type: string
attribute:
  description: Attribute from the source to monitor/compensate. When omitted the state value of the source will be used.
  required: false
  type: string
degree:
  description: "The degree of a polynomial. e.g., Linear compensation (y = x + 3) has 1 degree, Quadratic compensation (y = x<sup>2</sup> + x + 3) has 2 degrees, etc."
  required: false
  default: 1
  type: integer
precision:
  description: Defines the precision of the calculated values, through the argument of round().
  required: false
  default: 2
  type: integer
device_class:
  description: Defines the device_class of the sensor, if any. By default, the unit of measurement from the source will be used (except when `attribute` is specified). A list of device classes is available in the [sensors integration](/integrations/sensor).
  required: false
  type: string
unit_of_measurement:
  description: Defines the units of measurement of the sensor, if any. By default, the unit of measurement from the source will be used (except when `attribute` is specified).
  required: false
  type: string
hide_source:
  description: Hide the source entity in Home Assistant. If specified with `attribute`, it will hide the `source` entity as attributes cannot be hidden individually.
  required: false
  type: boolean
  default: false
{% endconfiguration %}
