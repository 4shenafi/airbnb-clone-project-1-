# 🎯 Use Case Diagram - StayBackend System

## 📋 System Actors

### Primary Actors
- **Guest**: Users who book and stay at properties
- **Host**: Property owners who list and manage properties
- **Admin**: System administrators who manage the platform

### Secondary Actors
- **Payment Gateway**: External payment processing system
- **Email Service**: External email notification service
- **SMS Service**: External SMS notification service

## 🔄 Use Case Diagram Description

```
                    StayBackend System
    ┌─────────────────────────────────────────────────────────┐
    │                                                         │
    │  ┌─────────────────┐    ┌─────────────────┐            │
    │  │     Guest       │    │      Host       │            │
    │  └─────────────────┘    └─────────────────┘            │
    │         │                        │                     │
    │         │                        │                     │
    │    ┌────▼────┐              ┌────▼────┐                │
    │    │ Register│              │ Register│                │
    │    │ Account │              │ Account │                │
    │    └─────────┘              └─────────┘                │
    │         │                        │                     │
    │         │                        │                     │
    │    ┌────▼────┐              ┌────▼────┐                │
    │    │  Login  │              │  Login  │                │
    │    └─────────┘              └─────────┘                │
    │         │                        │                     │
    │         │                        │                     │
    │    ┌────▼────┐              ┌────▼────┐                │
    │    │ Manage  │              │ Create  │                │
    │    │ Profile │              │Property │                │
    │    └─────────┘              │Listing  │                │
    │         │                   └─────────┘                │
    │         │                        │                     │
    │         │                        │                     │
    │    ┌────▼────┐              ┌────▼────┐                │
    │    │ Search  │              │ Manage  │                │
    │    │Properties│              │Property │                │
    │    └─────────┘              │Listing  │                │
    │         │                   └─────────┘                │
    │         │                        │                     │
    │         │                        │                     │
    │    ┌────▼────┐              ┌────▼────┐                │
    │    │ Book    │              │ View    │                │
    │    │Property │              │Bookings │                │
    │    └─────────┘              └─────────┘                │
    │         │                        │                     │
    │         │                        │                     │
    │    ┌────▼────┐              ┌────▼────┐                │
    │    │ Make    │              │ Respond │                │
    │    │Payment  │              │Reviews  │                │
    │    └─────────┘              └─────────┘                │
    │         │                        │                     │
    │         │                        │                     │
    │    ┌────▼────┐              ┌────▼────┐                │
    │    │ Leave   │              │ Manage  │                │
    │    │ Review  │              │Payments │                │
    │    └─────────┘              └─────────┘                │
    │         │                        │                     │
    │         │                        │                     │
    │    ┌────▼────┐              ┌────▼────┐                │
    │    │ Manage  │              │ View    │                │
    │    │Bookings │              │Analytics│                │
    │    └─────────┘              └─────────┘                │
    │                                                         │
    │  ┌─────────────────┐                                    │
    │  │     Admin       │                                    │
    │  └─────────────────┘                                    │
    │         │                                               │
    │         │                                               │
    │    ┌────▼────┐                                          │
    │    │ Manage  │                                          │
    │    │ Users   │                                          │
    │    └─────────┘                                          │
    │         │                                               │
    │         │                                               │
    │    ┌────▼────┐                                          │
    │    │ Moderate│                                          │
    │    │Content  │                                          │
    │    └─────────┘                                          │
    │         │                                               │
    │         │                                               │
    │    ┌────▼────┐                                          │
    │    │ View    │                                          │
    │    │Analytics│                                          │
    │    └─────────┘                                          │
    │         │                                               │
    │         │                                               │
    │    ┌────▼────┐                                          │
    │    │ Manage  │                                          │
    │    │System   │                                          │
    │    └─────────┘                                          │
    │                                                         │
    └─────────────────────────────────────────────────────────┘
```

## 📝 Detailed Use Cases

### 👤 Guest Use Cases

#### UC-001: Register Account
- **Actor**: Guest
- **Description**: Guest creates a new account on the platform
- **Preconditions**: Guest has valid email address
- **Main Flow**:
  1. Guest accesses registration page
  2. Guest enters personal information (name, email, password)
  3. System validates information
  4. System sends verification email
  5. Guest clicks verification link
  6. System activates account
- **Postconditions**: Guest account is created and activated

#### UC-002: Login
- **Actor**: Guest
- **Description**: Guest authenticates to access the platform
- **Preconditions**: Guest has an active account
- **Main Flow**:
  1. Guest enters email and password
  2. System validates credentials
  3. System generates JWT token
  4. System grants access to platform
- **Postconditions**: Guest is logged in and can access platform features

#### UC-003: Search Properties
- **Actor**: Guest
- **Description**: Guest searches for available properties
- **Preconditions**: Guest is logged in
- **Main Flow**:
  1. Guest enters search criteria (location, dates, guests)
  2. System queries property database
  3. System returns matching properties
  4. Guest can filter and sort results
- **Postconditions**: Guest views list of available properties

#### UC-004: Book Property
- **Actor**: Guest
- **Description**: Guest makes a booking for a property
- **Preconditions**: Guest is logged in, property is available
- **Main Flow**:
  1. Guest selects property and dates
  2. System calculates total cost
  3. Guest enters payment information
  4. System processes payment
  5. System creates booking
  6. System sends confirmation
- **Postconditions**: Booking is created and confirmed

#### UC-005: Leave Review
- **Actor**: Guest
- **Description**: Guest leaves a review after their stay
- **Preconditions**: Guest has completed a stay
- **Main Flow**:
  1. Guest accesses review page
  2. Guest rates property (1-5 stars)
  3. Guest writes review text
  4. Guest submits review
  5. System publishes review
- **Postconditions**: Review is published and visible to other users

### 🏠 Host Use Cases

#### UC-006: Create Property Listing
- **Actor**: Host
- **Description**: Host creates a new property listing
- **Preconditions**: Host is logged in and verified
- **Main Flow**:
  1. Host accesses "List Property" page
  2. Host enters property details (title, description, location)
  3. Host uploads property photos
  4. Host sets pricing and availability
  5. Host submits listing
  6. System reviews and approves listing
- **Postconditions**: Property listing is created and published

#### UC-007: Manage Property Listing
- **Actor**: Host
- **Description**: Host updates property listing information
- **Preconditions**: Host owns the property listing
- **Main Flow**:
  1. Host accesses property management page
  2. Host selects property to edit
  3. Host updates property information
  4. Host saves changes
  5. System updates listing
- **Postconditions**: Property listing is updated with new information

#### UC-008: View Bookings
- **Actor**: Host
- **Description**: Host views all bookings for their properties
- **Preconditions**: Host is logged in
- **Main Flow**:
  1. Host accesses booking management page
  2. System retrieves all bookings for host's properties
  3. Host can filter by property, date, or status
  4. Host views booking details
- **Postconditions**: Host views comprehensive booking information

#### UC-009: Respond to Reviews
- **Actor**: Host
- **Description**: Host responds to guest reviews
- **Preconditions**: Host has received a review
- **Main Flow**:
  1. Host accesses review management page
  2. Host selects review to respond to
  3. Host writes response
  4. Host submits response
  5. System publishes response
- **Postconditions**: Host response is published and visible

### 👨‍💼 Admin Use Cases

#### UC-010: Manage Users
- **Actor**: Admin
- **Description**: Admin manages user accounts and permissions
- **Preconditions**: Admin is logged in with admin privileges
- **Main Flow**:
  1. Admin accesses user management page
  2. Admin views user list
  3. Admin can suspend, activate, or delete users
  4. Admin can modify user roles and permissions
  5. System updates user status
- **Postconditions**: User accounts are managed according to admin actions

#### UC-011: Moderate Content
- **Actor**: Admin
- **Description**: Admin reviews and moderates platform content
- **Preconditions**: Admin is logged in with admin privileges
- **Main Flow**:
  1. Admin accesses content moderation page
  2. Admin reviews reported content
  3. Admin approves or rejects content
  4. Admin can remove inappropriate content
  5. System updates content status
- **Postconditions**: Platform content is moderated and appropriate

#### UC-012: View Analytics
- **Actor**: Admin
- **Description**: Admin views platform analytics and reports
- **Preconditions**: Admin is logged in with admin privileges
- **Main Flow**:
  1. Admin accesses analytics dashboard
  2. System displays key metrics and statistics
  3. Admin can filter data by date, region, or other criteria
  4. Admin can generate custom reports
- **Postconditions**: Admin has access to comprehensive platform analytics

## 🔗 Use Case Relationships

### Include Relationships
- **Make Payment** includes **Validate Payment Information**
- **Book Property** includes **Check Availability**
- **Create Property Listing** includes **Upload Photos**

### Extend Relationships
- **Book Property** extends **Search Properties** (when guest finds property)
- **Leave Review** extends **Manage Bookings** (after stay completion)
- **Respond to Reviews** extends **View Bookings** (when review is received)

### Generalization Relationships
- **Guest** and **Host** are both types of **User**
- **Create Property Listing** and **Manage Property Listing** are both types of **Property Management**

## 🎯 Use Case Priorities

### High Priority (Core Features)
1. Register Account
2. Login
3. Search Properties
4. Book Property
5. Create Property Listing
6. Make Payment

### Medium Priority (Enhanced Features)
1. Leave Review
2. Manage Property Listing
3. View Bookings
4. Respond to Reviews
5. Manage Users

### Low Priority (Advanced Features)
1. Moderate Content
2. View Analytics
3. Manage System

---

**This use case diagram provides a comprehensive view of all user interactions with the StayBackend system, ensuring that all stakeholder needs are addressed in the system design.**
