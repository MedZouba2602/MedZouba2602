erDiagram
    Residence {
        int Id PK
        string Block
        int FloorNumber
        string FlatNumber
        string Status
        int NumberOfRooms
        int NumberOfResidents
        string ResidentName
    }
    Residents {
        int Id PK
        string Name
        int Age
        int ResidenceId FK
    }
    Payments {
        int Id PK
        decimal Amount
        date PaymentDate
        int ResidentId FK
    }
    Users {
        int Id PK
        string UserName
        string Password
        int ResidenceId FK
        int DepartmentId FK
    }
    Department {
        int Id PK
        string DepartmentName
    }
    Facilities {
        int Id PK
        string FacilityName
        int ResidenceId FK
    }
    EntryExit {
        int Id PK
        datetime EntryTime
        datetime ExitTime
        int ResidenceId FK
    }
    FacilitiesMembership {
        int Id PK
        int ResidentId FK
        int FacilityId FK
        date MembershipDate
    }

    Residence ||--o{ Residents: contains
    Residence ||--o{ Facilities: contains
    Residence ||--o{ Users: contains
    Residence ||--o{ EntryExit: contains
    Residents ||--o{ Payments: makes
    Residents ||--o{ FacilitiesMembership: has
    Users }|--|| Department: works_in
    FacilitiesMembership }|--|| Facilities: uses
    FacilitiesMembership }|--|| Residents: involves
