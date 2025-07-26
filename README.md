SELECT 
    (SELECT COUNT(*) 
     FROM ami_master.survey_output 
     WHERE survey_timings <= '2024-08-01 23:59:59') AS meter_number,
    (SELECT COUNT(*) 
     FROM ami_master.dt_meter_installation_data 
     WHERE surveyed_date <= '2024-08-01 23:59:59') AS new_meter_serial_number,
    (SELECT COUNT(*) 
     FROM ami_master.survey_output 
     WHERE survey_timings <= '2024-08-01 23:59:59') + 
    (SELECT COUNT(*) 
     FROM ami_master.dt_meter_installation_data 
     WHERE surveyed_date <= '2024-08-01 23:59:59') AS total_count;
