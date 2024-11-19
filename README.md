# Sample-Performance-Testing-Project
This is a sample JMeter test script for performance testing JPetStore that integrates with InfluxDB and Grafana. 

To create a sample JMeter test script for JPetStore integrated with InfluxDB and Grafana for performance testing, you'll need to configure JMeter to send the test results to an InfluxDB database, where Grafana will retrieve and visualize the data. Here's an outline of the process, followed by a basic script example.

# Steps
# JMeter Setup:
You'll need the Backend Listener for InfluxDB in JMeter. You can install this via the JMeter Plugins Manager.
![Image 2](https://github.com/user-attachments/assets/51729116-b1c0-4d7e-927a-31908ae89560)


# InfluxDB Setup:
* Run the InfluxDB container in detached mode.
  ```
  docker run -d --name=influxdb -p 8086:8086 influxdb
  ```
* After the container is running, you can access the InfluxDB API at via http://localhost:8086.
* Then configure InfluxDB. You can configure InfluxDB using its configuration files or through its API.
* Generate an API Token. InfluxDB uses tokens for authentication. You can generate a token by sending a request to the appropriate API endpoint or through the InfluxDB UI if you have it set up.
* Then configure JMeter to send its metrics to InfluxDB.  Add a Backend Listener to your Jmeter test plan. and then run Your JMeter test, it will send metrics to the specified InfluxDB database.
  ![3](https://github.com/user-attachments/assets/b23be8a4-0583-4ea9-be78-5f7c63026180)


# Grafana Setup:
* Run a Grafana container in detached mode.
  ```
  docker run -d --name=grafana -p 3000:3000 grafana/grafana
  ```
* After running this command, you can access Grafana by going to http://localhost:3000 in your web browser.
* Create a dashboard in Grafana to visualize metrics such as response times, throughput, error rates, etc.
  
![Dashboard](https://github.com/user-attachments/assets/d8786081-7d8b-4b7b-a6cc-234ee2339bfc)
  
![6](https://github.com/user-attachments/assets/8211fbf6-40ca-476d-8fcb-98dbb2dc2505)

Note:
If you have a specific dashboard template in mind for JMeter performance testing, you can find its ID from the Grafana dashboard repository or from a trusted source like Grafana Labs. You can import dashboard, You can either upload a JSON file of the dashboard or use a dashboard ID.
* Copy the dashboard ID (e.g., 12345) from Grafana Labs.
* Then go to Grafana > click the 'New' button > click the 'Import'
* Paste the ID in the 'Import via ID' field.
* Click the "Load" button.
* Once imported, you can view and customize your dashboard as needed.

![Screenshot 2024-10-19 171057](https://github.com/user-attachments/assets/db2579b4-48e9-4fa7-bc32-859d113acb5c)


# JPetStore:
URL: https://petstore.octoperf.com/actions/Catalog.action
This app provides a e-commerce shopping cart.The JMeter script will simulate user actions such as browsing items, adding them to the cart, and placing orders.

# Test Plan for the JPetStore
JMeter Test Plan is the root for all tests.
* Home_Page
* Register_Page
* Login_Page
* Create_An_Order
* Submit_Payment _Details
* My_Accounts
* Sign_Out

Note: 
* CSV Data Set Config- points to a csv file login_info.csv containing all the login and passwords of the simulated users. 
* HTTP Requests are grouped within transaction controllers to provide meaningful metrics during the performance test. 

![jmeter](https://github.com/user-attachments/assets/f336881b-e856-4afc-8fd0-64d1ca774f7d)





