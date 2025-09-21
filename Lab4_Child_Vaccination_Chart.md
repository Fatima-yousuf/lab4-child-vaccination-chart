# Lab 4: Child Vaccination Chart
## Objective
### Main dictionary to store patient records
```python
patient = {}
# List of vaccines based on the Google Sheet
vaccines = ["HepB", "RV", "DTaP", "Hib", "PCV13", "IPV", "IIV4", "MMR", "VAR", "HepA"]
def insert():
    """
    This function takes user input for a patient's first name, last name,
    and the months for each vaccine. It stores the information in a nested
    dictionary under a unique record number.
    """
    # Determine the next available record number
    if patient:
        record_number = max(patient.keys()) + 1
    else:
        record_number = 1

    # Get patient basic information
    first_name = input("Enter patient's first name: ")
    last_name = input("Enter patient's last name: ")

    # Dictionary to store vaccine information for this patient
    vaccine_info = {}

    # Loop through each vaccine and get months from user
    for vac in vaccines:
        while True:
            months_input = input(f"Enter months for {vac} (comma-separated, e.g., 0,1,6) or leave blank if none: ")
            if months_input.strip() == "":
                vaccine_info[vac] = []
                break
            try:
                # Convert comma-separated string to list of integers
                month_list = [int(m.strip()) for m in months_input.split(",")]
                vaccine_info[vac] = month_list
                break
            except ValueError:
                print("Invalid input. Please enter numbers separated by commas.")

    # Create the nested dictionary for this patient
    patient_record = {
        "First Name": first_name,
        "Last Name": last_name,
        "Vaccines": vaccine_info
    }

    # Add patient record to the main dictionary
    patient[record_number] = patient_record
    print(f"\nPatient record added successfully with record number {record_number}!\n")

# -----------------------------
# Example usage
# -----------------------------
print("### Child Vaccination Chart ###\n")

# Insert first patient
insert()

# Insert second patient
insert()

# Display all patient records to verify
print("### All Patient Records ###")
for record, details in patient.items():
    print(f"\nRecord {record}:")
    print(f"Name: {details['First Name']} {details['Last Name']}")
    print("Vaccines:")
    for vac, months in details["Vaccines"].items():
        print(f"  {vac}: {months}")
# Verification of Patient Records
### All Patient Records ###

Record 1:
Name: John Smith
Vaccines:
  HepB: [0, 1, 6]
  RV: [0, 1, 6]
  DTaP: [0, 1, 6]
  Hib: [0, 1, 6]
  PCV13: [0, 1, 6]
  IPV: [0, 1, 6]
  IIV4: [0, 1, 6]
  MMR: [0, 1, 6]
  VAR: [0, 1, 6]
  HepA: [0, 1, 6]

Record 2:
Name: Olivia James
Vaccines:
  HepB: [0, 1, 6]
  RV: [0, 1, 6]
  DTaP: [0, 1, 6]
  Hib: [0, 1, 6]
  PCV13: [0, 1, 6]
  IPV: [0, 1, 6]
  IIV4: [0, 1, 6]
  MMR: [0, 1, 6]
  VAR: [0, 1, 6]
  HepA: [0, 1, 6]
```

