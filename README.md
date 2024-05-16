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

## Pros and Cons

### Pros

- Streamline business operations by automating order placement and tracking processes.
- Enhance customer experience with real-time shipment tracking.
- Access to comprehensive shipping rate information for better decision making.

### Cons

- Initial setup and integration may require technical expertise.
- Maintenance and updates to API integration may be necessary over time.

## What to be Aware of

- Ensure compliance with API usage guidelines and terms.
- Implement robust error handling mechanisms to handle potential issues.
- Regularly monitor API performance and usage metrics to ensure optimal functionality.

## Considerations

- Maintain open communication channels with J&T Express support teams for assistance and guidance.
- Stay updated with any changes or updates to the API documentation provided by J&T Express.
- Plan for scalability and future enhancements in your API integration strategy.

## Conclusion

Integrating with J&T Express APIs offers businesses a powerful tool to streamline their logistics and shipping processes. By leveraging these APIs, companies can automate order placement, track shipments in real-time, and access vital tariff information for informed decision-making. While there are initial challenges in setup and maintenance, the benefits of enhanced efficiency and customer satisfaction outweigh these drawbacks.

To ensure successful integration, it's crucial to follow the implementation planning steps outlined in this guide, maintain compliance with API usage guidelines, and stay updated with any changes or updates provided by J&T Express. By doing so, businesses can maximize the potential of their API integration and drive growth in their operations.

For comprehensive API usage instructions, examples, and error code descriptions, refer to the provided documentation available at [J&T Express Developer Documentation](https://developer.jet.co.id/documentation).
