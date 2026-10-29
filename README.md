# 🚇 Metro Ticket Generating System in ServiceNow

A ServiceNow application that streamlines metro ticket booking through automated fare calculation, booking validation, ticket number generation, booking confirmation, and digital ticket data generation.

## 📌 Project Overview

The **Metro Ticket Generating System** is a custom application developed on the ServiceNow platform to demonstrate how platform capabilities can be used to automate a transportation ticket-booking workflow.

The application allows passenger booking details and journey information to be recorded, calculates fares based on configured fare rules, generates ticket numbers, validates bookings, and updates booking status through Flow Designer.

The project demonstrates the practical use of ServiceNow tables, Business Rules, server-side scripting, Flow Designer, Service Catalog, and UI Builder.

## 🎯 Problem Statement

Traditional ticket-booking workflows can involve repetitive data entry, manual fare calculations, and inefficient ticket management.

This project explores how these activities can be streamlined through a centralized ServiceNow application that automates booking-related operations and presents ticket information digitally.

## ✨ Key Features

- **Metro Station Management:** Maintains station names, station codes, sequence numbers, and active status.
- **Ticket Booking:** Captures passenger details, source and destination stations, journey date, and passenger count.
- **Automatic Fare Calculation:** Calculates fares using configurable fare rules.
- **Unique Ticket Number Generation:** Automatically generates a ticket number for each booking.
- **Booking Validation:** Rejects invalid bookings, including identical source and destination stations, passenger counts below one, and past journey dates.
- **Automated Booking Confirmation:** Uses ServiceNow Flow Designer to update booking status.
- **Dynamic Digital Ticket:** Displays actual booking information retrieved from the selected Metro Tickets Booking record.
- **Dynamic QR Code:** Generates a QR image using the selected booking's QR data, allowing the displayed QR code to correspond to the ticket.
- **Data-Driven UI Builder Page:** Uses a ServiceNow data resource and dynamic data binding to connect booking records to the digital ticket interface.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| ServiceNow Platform | Application development environment |
| Custom Tables | Stores station, fare-rule, and booking information |
| Business Rules | Implements fare calculation, ticket number generation, and booking validation |
| Server-side JavaScript | Implements backend processing and automation logic |
| Flow Designer | Automates booking confirmation |
| Service Catalog | Supports the ticket-booking request experience |
| UI Builder | Builds the digital ticket user interface |
| QR Code Service | Used for testing QR image generation from ticket data |

## 🏗️ Application Architecture

The application follows a straightforward booking workflow:

1. **Booking Input:** The passenger's journey and personal details are submitted.
2. **Validation:** Booking information is checked against the configured validation rules.
3. **Fare Calculation:** A Business Rule calculates the fare using the active fare rule.
4. **Ticket Generation:** A ticket number is generated and associated with the booking.
5. **Booking Confirmation:** Flow Designer updates the booking status.
6. **QR Payload Generation:** Ticket details are assembled into a QR data payload.
7. **Digital Ticket Display:** The digital ticket interface presents the booking information.

### Workflow

```text
Passenger Booking
       |
       v
Validate Booking Details
       |
       v
Calculate Fare
       |
       v
Generate Ticket Number
       |
       v
Save Booking Record
       |
       v
Flow Designer Confirmation
       |
       v
Generate QR Data Payload
       |
       v
Display Digital Ticket
```

## 🗃️ Data Model

### 1. Metro Station

Stores metro station details.

Representative fields:
- Station Name
- Station Code
- Station Sequence

## 📱 Digital Ticket and QR Code Generation

The application provides a digital ticket interface built using ServiceNow UI Builder. Rather than displaying fixed demonstration values, the page retrieves the selected booking record and displays its relevant information dynamically.

The digital ticket includes:
- Passenger name
- Unique ticket number
- Source and destination stations
- Journey date
- Passenger count
- Total fare
- Booking status
- QR code associated with the booking data

### How it works

1. A passenger booking is created and processed by the application.
2. Business Rules calculate the fare, generate the ticket number, and prepare the QR data payload.
3. Flow Designer updates the booking status.
4. The digital ticket page retrieves the relevant booking record using its record identifier (`sysId`).
5. UI Builder dynamically displays the booking details.
6. The QR image is generated from the corresponding booking's QR data.

This approach demonstrates how ServiceNow data resources and dynamic data binding can be used to create a record-specific user interface.

**Note:** The QR code currently represents ticket information for demonstration purposes. It does not provide verification against a live metro operator or an actual metro-gate scanning system.

## 🎥 Project Demo

Watch the Metro Ticket Generating System demonstration:

[▶️ View the project demo](https://drive.google.com/file/d/14D1Od92QSr82xeMNpwBX5FkPQE21zVk3/view?usp=drivesdk)

The demonstration covers ticket booking, automatic fare calculation, ticket number generation, booking confirmation, and the dynamic digital ticket with its QR code.

## 🧪 Testing

The following scenarios were tested during development:

| Test Scenario | Expected Result |
|---|---|
| Valid booking | Booking record is created successfully |
| Automatic fare calculation | Fare is calculated using configured fare rules |
| Ticket number generation | A ticket number is generated |
| Identical source and destination | Booking is rejected |
| Passenger count below one | Booking is rejected |
| Past journey date | Booking is rejected |
| Booking confirmation | Status changes to Confirmed |
| QR payload generation | Ticket data is stored in the QR Code Data field |
| Dynamic ticket details | Digital ticket displays information from the selected booking |
| Dynamic QR image | QR image corresponds to the selected booking's QR data |
| Different booking records | Ticket details and QR data change according to the selected record |

## 🔮 Future Enhancements

Potential improvements include:

- Secure ticket verification through a dedicated validation endpoint
- Integration with an actual metro operator or ticket-scanning system
- Verified email notifications when outbound email is configured
- Payment gateway integration
- Ticket cancellation and refund workflows
- More comprehensive role-based access control
- Additional accessibility and mobile usability improvements

These enhancements are outside the scope of the current prototype.
