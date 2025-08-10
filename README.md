# J&T Express API Integration Guide

## Overview and Summary

Welcome to the J&T Express API Integration Guide. This document provides comprehensive information on integrating with J&T Express APIs to enhance your business operations. From placing orders to tracking shipments and tariff checking, this guide covers all aspects of API integration with J&T Express.

## Function and Implementation Planning

### Functions of J&T Express APIs

1. **Basic Order API**: Place orders from marketplaces or ecommerce platforms to J&T Express.
2. **Tracking API**: Track shipment progress and status in real-time.
3. **Tariff Checking API**: Check shipping rates from origin city to destination district.
4. **API Cancel Order**: Cancel orders that have not been processed by J&T Express.

### Implementation Planning

1. **Start**: Fill Information Form and select required APIs.
2. **Cooperation Agreement**: Establish an agreement between Client and J&T Agent.
3. **Test API Integration**: Integrate test/sandbox APIs and perform testing on J&T testing environment.
4. **Mapping Process**: Map client's data with J&T's list of districts, cities, and provinces if required.
5. **Production API Integration**: Use production key and endpoint for final testing.
6. **Finish**: Complete all steps and ensure the API is connected to the J&T platform.

## Usage Cases
### 1. E-commerce Order Fulfillment Automation
**Scenario:** An online marketplace wants to automatically create shipping orders with J&T Express whenever customers place purchases.

- When a customer completes checkout on the e-commerce platform, the system automatically sends a **Basic Order API** request to J&T with shipping details.
- J&T returns an Air Waybill (AWB) number via API.
- The platform displays the AWB number to the customer for tracking purposes.
- The system tracks the shipment status using the **Tracking API** to update customers in real-time.
- If the customer cancels the order before shipment, the platform uses the **API Cancel Order**.
This use case automates order processing, reduces manual entry, and improves customer service.

### 2. Real-time Shipment Tracking for Customer Support
**Scenario:** A customer service team needs instant access to the latest shipment status when handling inquiries.
- Customer support queries the **Tracking API** using the AWB to fetch real-time package location and status.
- They respond accurately to customers about estimated delivery times or delays.
- Automated alerts can be set up based on tracking status updates received from J&T APIs.
This use case improves support efficiency and customer satisfaction by providing up-to-date information.

### 3. Shipping Rate Estimation for Checkout
**Scenario:** An online store wants to display accurate shipping costs to customers before order submission.
- At checkout, the platform sends an origin and destination city/district to the **Tariff Checking API**.
- Receives shipping rates and estimated delivery times.
- Displays available shipping service options and costs in the UI.
- The customer selects a shipping service based on rates/ETD provided by J&T.
This use case enhances the checkout experience with transparent shipping costs and options.

### 4. Order Cancellation Before Shipment
**Scenario:** A merchant needs to cancel an order that has been placed via the API but not yet processed by J&T.
- The merchant calls the **API Cancel Order** passing the order ID.
- J&T confirms whether cancellation was successful or if the order has already progressed beyond cancelable status.
- The merchant updates the order status accordingly in their system.
This use case provides flexibility for merchants to manage shipments and customer expectations.

## Sequence diagram
<img width="1026" height="646" alt="gleek-VnUvmwuzjC67KndwXgEDuw" src="https://github.com/user-attachments/assets/9056aa85-2ec5-4932-a169-079ee1fe2feb" />

The sequence diagram you provided outlines the flow of interactions in a typical J&T Express API integration scenario between a User (Customer), an E-commerce platform (Ecom), and J&T Express (JNT). Here’s an explanation of each step:

1. **User - Customer Order -> Ecom**  
   The customer places an order on the e-commerce platform. This triggers the process of preparing the order for shipment.

2. **Ecom - Ecom Request API -> JNT**  
   The e-commerce platform sends an API request to J&T Express to create a shipment order. This request typically includes shipment details such as sender and receiver information, package details, and service type.

3. **JNT - Return AWB Number -> Ecom**  
   J&T Express processes the order request and responds by returning an Air Waybill (AWB) number. The AWB number is a unique tracking code that identifies the shipment.

4. **Ecom - Return AWB Number -> User**  
   The e-commerce platform receives the AWB number from J&T and sends it back to the customer. This allows the customer to track their shipment using the AWB.

5. **User - Drop Off -> JNT**  
   Finally, the customer drops off the package at a J&T service point or arranges for pickup, handing over the physical shipment to J&T Express for delivery.

 
## Resource Requirements for J&T Express API Integration

### Technical Resources

- **API Developer(s):** Responsible for coding, integrating, and maintaining the API connections between your system and J&T Express.
- **QA/Test Engineer(s):** Conduct testing in sandbox and production environments to ensure API stability, correctness, and performance.
- **Development Environment and Tools:** Includes software, IDEs, testing tools, and repository management for development work.
- **Access to J&T Sandbox and Production API:** Credentials and environment access needed to develop and deploy integration.
- **Monitoring & Logging Tools:** Software to monitor API calls, track errors, and analyze performance.
- **Up-to-date API Documentation:** Technical references and documentation from J&T for accurate integration.

### Non-Technical Resources

- **Project Manager:** Oversees the integration process, coordinates between technical teams and stakeholders, manages timelines and deliverables.
- **Business Analyst:** Handles business requirement gathering, maps client data (e.g., locations) with J&T codes, and ensures alignment with operational needs.
- **Support Team:** Provides ongoing user support post-integration, manages communications with J&T support, and handles issue resolution.
- **Communication Channels:** Established flow of communication among client teams, J&T agents, and possibly third-party partners.
- **Legal/Contract Management:** Handles cooperation agreements and compliance with terms of service with J&T Express.

## Suggested Timeline for Integration

| Phase                        | Description                               | Duration         |
|------------------------------|-----------------------------------------|------------------|
| Preparation                  | Requirement collection and agreement    | 1-2 weeks        |
| API Access & Setup           | Get API keys, configure environment     | 1 week           |
| Development & Integration    | Coding, mapping data, initial integration | 2-3 weeks        |
| Testing                     | Functional and performance testing       | 2 weeks          |
| Production Deployment       | Final setup and go-live                   | 1 week           |
| Monitoring & Support        | Continuous after go-live                  | Ongoing          |


## Pros and Cons

### Pros

- Streamline business operations by automating order placement and tracking processes.
- Enhance customer experience with real-time shipment tracking.
- Access to comprehensive shipping rate information for better decision making.

### Cons

- Initial setup and integration may require technical expertise.
- Maintenance and updates to API integration may be necessary over time.


## Considerations

- Maintain open communication channels with J&T Express support teams for assistance and guidance.
- Stay updated with any changes or updates to the API documentation provided by J&T Express.
- Plan for scalability and future enhancements in your API integration strategy.

## Sample API Usage 
### Request Details

### Endpoint

- **URL**: Provided by the service provider
- **Method**: `POST`
- **Headers**: `Content-Type: application/json`

### Request Payload

```php
$key = "<< Please call us >>";
$data = array(
    'username' => 'username',
    'api_key' => 'api_key',
    'orderid' => 'ORDERID-0001',
    'shipper_name' => 'PENGIRIM',
    'shipper_contact' => 'PENGIRIM',
    'shipper_phone' => '+628123456789',
    'shipper_addr' => 'JL. Pengirim no.88, RT/RW:001/010, Pluit',
    'origin_code' => 'JKT',
    'receiver_name' => 'PENERIMA',
    'receiver_phone' => '+62812348888',
    'receiver_addr' => 'JL. Penerima no.1, RT/RW:04/07, Sidoarjo',
    'receiver_zip' => '40123',
    'destination_code' => 'JKT',
    'receiver_area' => 'JKT001',
    'qty' => '1',
    'weight' => '1',
    'goodsdesc' => 'TESTING!!',
    'servicetype' => '1',
    'insurance' => '122',
    'orderdate' => '2021-08-01 22:02:00',
    'item_name' => 'topi',
    'cod' => '120000',
    'sendstarttime' => '2021-08-01 08:00:00',
    'sendendtime' => '2021-08-01 22:00:00',
    'expresstype' => '1',
    'goodsvalue' => '1000'
);

$data_json = json_encode(array('detail' => array($data)));
$data_request = array(
    'data_param' => $data_json,
    'data_sign' => base64_encode(md5($data_json . $key))
);
```

### Example Request in PHP

```php
<?php

$key = "<< Please call us >>";
$data = array(
    // Add all required fields here
);

$data_json = json_encode(array('detail' => array($data)));
$data_request = array(
    'data_param' => $data_json,
    'data_sign' => base64_encode(md5($data_json . $key))
);

$ch = curl_init('API_ENDPOINT_URL');
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Type: application/json'));
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($data_request));

$response = curl_exec($ch);
curl_close($ch);

echo $response;
?>
```

## Response Details

### Success Response

```json
{
    "success": true,
    "desc": "Request berhasil",
    "detail": [
        {
            "awb_no": "JO0027364832",
            "orderid": "ORDERID-0001",
            "desCode": "JKT-JKT001",
            "etd": "2-4",
            "status": "Sukses"
        }
    ]
}
```

### Failed Response

```json
{
    "success": true,
    "desc": "Request berhasil",
    "detail": [
        {
            "orderid": "ORDERID-0001",
            "desCode": "JKT-JKT001",
            "etd": "No Data",
            "status": "Error",
            "reason": "Orderid tidak boleh sama"
        }
    ]
}
```

## Explanation of Fields

- `success`: Request processing status.
- `desc`: Description of the result.
- `detail`: Contains request details.
  - `awb_no`: Airway bill number (on success).
  - `orderid`: Order ID.
  - `desCode`: Destination code.
  - `etd`: Estimated delivery time.
  - `status`: "Sukses" or "Error".
  - `reason`: Error reason (on failure).


## Conclusion

Integrating with J&T Express APIs offers businesses a powerful tool to streamline their logistics and shipping processes. By leveraging these APIs, companies can automate order placement, track shipments in real-time, and access vital tariff information for informed decision-making. While there are initial challenges in setup and maintenance, the benefits of enhanced efficiency and customer satisfaction outweigh these drawbacks.

To ensure successful integration, it's crucial to follow the implementation planning steps outlined in this guide, maintain compliance with API usage guidelines, and stay updated with any changes or updates provided by J&T Express. By doing so, businesses can maximize the potential of their API integration and drive growth in their operations.

For comprehensive API usage instructions, examples, and error code descriptions, refer to the provided documentation available at [J&T Express Developer Documentation](https://developer.jet.co.id/documentation).
