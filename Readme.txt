# AWS IoT Device Shadow with Raspberry Pi

This project demonstrates connecting a Raspberry Pi to AWS IoT Core using a Device Shadow, publishing simulated temperature sensor readings, and triggering an AWS Lambda function that processes the data and sends alerts via Amazon SES.

## Components
- **Device script** (`device/Temperature_Sensing_Sending.py`)  
  Publishes simulated temperature readings to AWS IoT Core Device Shadow.

- **AWS Lambda function** (`lambda/lambda_process_logic.py`)  
  Processes temperature updates and sends SES email alerts if threshold is exceeded.

- **IAM policy** (`lambda/lambda_permission.json`)  
  Grants the Lambda function permissions for SES and CloudWatch logging.

- **Report** (`report/report.pdf`)  
  Contains implementation steps, screenshots, challenges, test cases, and latency measurements.

## How to Run
1. Register a Thing in AWS IoT Core, create certs & attach policy.
2. Place the downloaded certificates on your Raspberry Pi.
3. Update `Temperature_Sensing_Sending.py` with:
   - Your AWS IoT endpoint
   - Paths to cert/key/CA files
   - Your Thing name
4. Run the script:  
   ```bash
   python3 Temperature_Sensing_Sending.py
