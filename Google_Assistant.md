I don't use google Assistant but @genestealer has suggested this if you do:

(See below for a simplified option)

```
#################################################
# Google Assistant integration.
# Every now and again have to visit this link and lick TEST: https://console.actions.google.com/project/hassio-214617/accountlinking/
google_assistant:
  project_id: !secret google_assistant_project_id
  secure_devices_pin: !secret google_assistant_secure_devices_pin
  service_account: !include private/google_assistant_report_state_hassio_214617.json
  report_state: true
  entity_config:
    input_boolean.irrigation_cycle1_adjust_for_rainfall:
      expose: false
    input_boolean.irrigation_cycle1_adjust_for_temperature:
      expose: false
    input_text.irrigation_cycle1_name:
      expose: false
    input_boolean.irrigation_cycle1_running:
      expose: false
    input_boolean.irrigation_cycle1_schedule_enabled:
      expose: false
    input_boolean.irrigation_cycle1_schedule_today_only:
      expose: false
    input_datetime.irrigation_cycle1_start_time:
      expose: false
    input_boolean.irrigation_cycle1_wait_for_entity:
      expose: false
    input_number.irrigation_cycle1_zone1_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone10_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone11_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone12_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone13_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone14_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone15_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone16_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone2_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone3_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone4_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone5_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone6_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone7_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone8_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone9_duration_box:
      expose: false
    input_number.irrigation_cycle1_zone1_duration:
      expose: false
    input_number.irrigation_cycle1_zone10_duration:
      expose: false
    input_number.irrigation_cycle1_zone11_duration:
      expose: false
    input_number.irrigation_cycle1_zone12_duration:
      expose: false
    input_number.irrigation_cycle1_zone13_duration:
      expose: false
    input_number.irrigation_cycle1_zone14_duration:
      expose: false
    input_number.irrigation_cycle1_zone15_duration:
      expose: false
    input_number.irrigation_cycle1_zone16_duration:
      expose: false
    input_number.irrigation_cycle1_zone2_duration:
      expose: false
    input_number.irrigation_cycle1_zone3_duration:
      expose: false
    input_number.irrigation_cycle1_zone4_duration:
      expose: false
    input_number.irrigation_cycle1_zone5_duration:
      expose: false
    input_number.irrigation_cycle1_zone6_duration:
      expose: false
    input_number.irrigation_cycle1_zone7_duration:
      expose: false
    input_number.irrigation_cycle1_zone8_duration:
      expose: false
    input_number.irrigation_cycle1_zone9_duration:
      expose: false
    input_boolean.irrigation_cycle1_zone1_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone1_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone1_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone1_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone1_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone1_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone1_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone1_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone10_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone10_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone10_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone10_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone10_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone10_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone10_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone10_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone11_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone11_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone11_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone11_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone11_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone11_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone11_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone11_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone12_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone12_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone12_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone12_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone12_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone12_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone12_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone12_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone13_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone13_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone13_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone13_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone13_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone13_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone13_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone13_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone14_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone14_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone14_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone14_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone14_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone14_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone14_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone14_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone15_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone15_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone15_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone15_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone15_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone15_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone15_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone15_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone16_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone16_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone16_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone16_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone16_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone16_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone16_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone16_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone2_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone2_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone2_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone2_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone2_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone2_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone2_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone2_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone3_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone3_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone3_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone3_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone3_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone3_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone3_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone3_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone4_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone4_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone4_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone4_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone4_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone4_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone4_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone4_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone5_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone5_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone5_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone5_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone5_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone5_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone5_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone5_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone6_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone6_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone6_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone6_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone6_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone6_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone6_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone6_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone7_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone7_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone7_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone7_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone7_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone7_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone7_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone7_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone8_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone8_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone8_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone8_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone8_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone8_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone8_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone8_wed:
      expose: false
    input_boolean.irrigation_cycle1_zone9_every_day:
      expose: false
    input_boolean.irrigation_cycle1_zone9_fri:
      expose: false
    input_boolean.irrigation_cycle1_zone9_mon:
      expose: false
    input_boolean.irrigation_cycle1_zone9_sat:
      expose: false
    input_boolean.irrigation_cycle1_zone9_sun:
      expose: false
    input_boolean.irrigation_cycle1_zone9_thu:
      expose: false
    input_boolean.irrigation_cycle1_zone9_tue:
      expose: false
    input_boolean.irrigation_cycle1_zone9_wed:
      expose: false
    input_boolean.irrigation_cycle2_adjust_for_rainfall:
      expose: false
    input_boolean.irrigation_cycle2_adjust_for_temperature:
      expose: false
    input_text.irrigation_cycle2_name:
      expose: false
    input_boolean.irrigation_cycle2_running:
      expose: false
    input_boolean.irrigation_cycle2_schedule_enabled:
      expose: false
    input_boolean.irrigation_cycle2_schedule_today_only:
      expose: false
    input_datetime.irrigation_cycle2_start_time:
      expose: false
    input_boolean.irrigation_cycle2_wait_for_entity:
      expose: false
    input_number.irrigation_cycle2_zone1_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone10_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone11_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone12_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone13_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone14_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone15_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone16_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone2_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone3_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone4_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone5_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone6_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone7_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone8_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone9_duration_box:
      expose: false
    input_number.irrigation_cycle2_zone10_duration:
      expose: false
    input_number.irrigation_cycle2_zone11_duration:
      expose: false
    input_number.irrigation_cycle2_zone12_duration:
      expose: false
    input_number.irrigation_cycle2_zone13_duration:
      expose: false
    input_number.irrigation_cycle2_zone14_duration:
      expose: false
    input_number.irrigation_cycle2_zone15_duration:
      expose: false
    input_number.irrigation_cycle2_zone16_duration:
      expose: false
    input_number.irrigation_cycle2_zone1_duration:
      expose: false
    input_number.irrigation_cycle2_zone2_duration:
      expose: false
    input_number.irrigation_cycle2_zone3_duration:
      expose: false
    input_number.irrigation_cycle2_zone4_duration:
      expose: false
    input_number.irrigation_cycle2_zone5_duration:
      expose: false
    input_number.irrigation_cycle2_zone6_duration:
      expose: false
    input_number.irrigation_cycle2_zone7_duration:
      expose: false
    input_number.irrigation_cycle2_zone8_duration:
      expose: false
    input_number.irrigation_cycle2_zone9_duration:
      expose: false
    input_boolean.irrigation_cycle2_zone1_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone1_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone1_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone1_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone1_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone1_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone1_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone1_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone10_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone10_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone10_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone10_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone10_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone10_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone10_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone10_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone11_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone11_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone11_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone11_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone11_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone11_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone11_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone11_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone12_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone12_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone12_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone12_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone12_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone12_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone12_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone12_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone13_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone13_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone13_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone13_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone13_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone13_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone13_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone13_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone14_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone14_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone14_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone14_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone14_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone14_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone14_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone14_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone15_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone15_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone15_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone15_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone15_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone15_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone15_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone15_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone16_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone16_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone16_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone16_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone16_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone16_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone16_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone16_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone2_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone2_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone2_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone2_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone2_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone2_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone2_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone2_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone3_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone3_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone3_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone3_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone3_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone3_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone3_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone3_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone4_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone4_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone4_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone4_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone4_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone4_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone4_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone4_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone5_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone5_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone5_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone5_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone5_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone5_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone5_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone5_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone6_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone6_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone6_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone6_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone6_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone6_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone6_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone6_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone7_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone7_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone7_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone7_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone7_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone7_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone7_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone7_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone8_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone8_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone8_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone8_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone8_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone8_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone8_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone8_wed:
      expose: false
    input_boolean.irrigation_cycle2_zone9_every_day:
      expose: false
    input_boolean.irrigation_cycle2_zone9_fri:
      expose: false
    input_boolean.irrigation_cycle2_zone9_mon:
      expose: false
    input_boolean.irrigation_cycle2_zone9_sat:
      expose: false
    input_boolean.irrigation_cycle2_zone9_sun:
      expose: false
    input_boolean.irrigation_cycle2_zone9_thu:
      expose: false
    input_boolean.irrigation_cycle2_zone9_tue:
      expose: false
    input_boolean.irrigation_cycle2_zone9_wed:
      expose: false
    input_text.irrigation_cycle3_name:
      expose: false
    input_boolean.irrigation_cycle3_running:
      expose: false
    input_number.irrigation_cycle3_zone1_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone10_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone11_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone12_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone13_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone14_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone15_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone16_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone2_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone3_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone4_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone5_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone6_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone7_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone8_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone9_duration_box:
      expose: false
    input_number.irrigation_cycle3_zone1_duration:
      expose: false
    input_number.irrigation_cycle3_zone10_duration:
      expose: false
    input_number.irrigation_cycle3_zone11_duration:
      expose: false
    input_number.irrigation_cycle3_zone12_duration:
      expose: false
    input_number.irrigation_cycle3_zone13_duration:
      expose: false
    input_number.irrigation_cycle3_zone14_duration:
      expose: false
    input_number.irrigation_cycle3_zone15_duration:
      expose: false
    input_number.irrigation_cycle3_zone16_duration:
      expose: false
    input_number.irrigation_cycle3_zone2_duration:
      expose: false
    input_number.irrigation_cycle3_zone3_duration:
      expose: false
    input_number.irrigation_cycle3_zone4_duration:
      expose: false
    input_number.irrigation_cycle3_zone5_duration:
      expose: false
    input_number.irrigation_cycle3_zone6_duration:
      expose: false
    input_number.irrigation_cycle3_zone7_duration:
      expose: false
    input_number.irrigation_cycle3_zone8_duration:
      expose: false
    input_number.irrigation_cycle3_zone9_duration:
      expose: false
    automation.irrigation_about_cycle_wifi_interruption:
      expose: false
    input_select.irrigation_cycle:
      expose: false
    input_text.irrigation_cycle1_wait_for_entity_name:
      expose: false
    input_text.irrigation_cycle1_wait_for_entity_state:
      expose: false
    input_boolean.irrigation_cycle1_wait_for_entity_name_timeout_continue:
      expose: false
    input_number.irrigation_cycle1_wait_for_entity_name_timeout_duration:
      expose: false
    input_text.irrigation_cycle2_wait_for_entity_name:
      expose: false
    input_text.irrigation_cycle2_wait_for_entity_state:
      expose: false
    input_boolean.irrigation_cycle2_wait_for_entity_name_timeout_continue:
      expose: false
    input_number.irrigation_cycle2_wait_for_entity_name_timeout_duration:
      expose: false
    automation.irrigation_cycle1_start_time_sunrise_offset:
      expose: false
    automation.irrigation_cycle1_start_time_sunset_offset:
      expose: false
    input_select.irrigation_cycle1_start_time_type:
      expose: false
    automation.irrigation_cycle2_start_time_sunrise_offset:
      expose: false
    automation.irrigation_cycle2_start_time_sunset_offset:
      expose: false
    input_select.irrigation_cycle2_start_time_type:
      expose: false
    automation.irrigation_notify_about_cycle_wifi_interruption:
      expose: false
    automation.irrigation_notify_when_cycle_starts_or_stops_2:
      expose: false
    automation.irrigation_notify_when_cycle_starts_or_stops:
      expose: false
    input_text.irrigation_previous_run_cycle_name:
      expose: false
    automation.irrigation_triggered_cycle_start:
      expose: false
    automation.irrigation_ui_set_default_cycle_names:
      expose: false
    group.irrigation_group_cycle1_every_day:
      expose: false
    group.irrigation_group_cycle1_fri:
      expose: false
    group.irrigation_group_cycle1_mon:
      expose: false
    group.irrigation_group_cycle1_sat:
      expose: false
    group.irrigation_group_cycle1_sun:
      expose: false
    group.irrigation_group_cycle1_thu:
      expose: false
    group.irrigation_group_cycle1_tue:
      expose: false
    group.irrigation_group_cycle1_wed:
      expose: false
    group.irrigation_group_cycle1_zone_durations:
      expose: false
    group.irrigation_group_cycle2_every_day:
      expose: false
    group.irrigation_group_cycle2_fri:
      expose: false
    group.irrigation_group_cycle2_mon:
      expose: false
    group.irrigation_group_cycle2_sat:
      expose: false
    group.irrigation_group_cycle2_sun:
      expose: false
    group.irrigation_group_cycle2_thu:
      expose: false
    group.irrigation_group_cycle2_tue:
      expose: false
    group.irrigation_group_cycle2_wed:
      expose: false
    group.irrigation_group_cycle2_zone_durations:
      expose: false
    group.irrigation_group_cycle3_zone_durations:
      expose: false
    input_boolean.irrigation_ui_show_cycle1:
      expose: false
    input_boolean.irrigation_ui_show_cycle2:
      expose: false
    input_boolean.irrigation_ui_show_cycle3:
      expose: false
    input_number.irrigation_cycle1_start_time_sunrise_offset:
      expose: false
    input_number.irrigation_cycle2_start_time_sunrise_offset:
      expose: false
    input_number.irrigation_cycle1_start_time_sunset_offset:
      expose: false
    input_number.irrigation_cycle2_start_time_sunset_offset:
      expose: false
    sensor.irrigation_cycle1_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_start_time_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone1_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone2_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone3_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone4_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone5_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone6_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone7_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone8_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_start_time_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone1_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone10_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone10_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone11_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone11_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone12_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone12_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone13_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone13_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone14_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone14_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone15_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone15_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone16_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone16_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone2_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone3_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone4_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone5_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone6_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone7_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone8_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle1_zone9_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle2_zone9_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone1_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone10_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone11_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone12_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone13_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone14_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone15_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone16_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone2_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone3_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone4_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone5_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone6_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone7_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone8_actual_duration_in_seconds:
      expose: false
    sensor.irrigation_cycle3_zone9_actual_duration_in_seconds:
      expose: false
    binary_sensor.irrigation_cycle_start_clash:
      expose: false
```

---------------

Simplified, add the data to a separate file and use entity_config: !include_dir_named 

Example:
```
google_assistant:
 project_id: !secret google_assistant_project_id
 secure_devices_pin: !secret google_assistant_secure_devices_pin
 service_account: !include private/google_assistant_report_state_hassio_214617.json
 report_state: true
 entity_config: !include_dir_named google_assistant_entity_config.yaml
```
