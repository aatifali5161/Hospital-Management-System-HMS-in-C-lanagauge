# Hospital-Management-System-HMS-in-C-lanagauge
he Hospital Management System (HMS) is a computerized system designed to  manage the daily operations of a hospital efficiently. This project integrates  multiple modules such as Patient Management, Doctor Management,  Appointment Management, Pharmacy &amp; Medical Management, and Billing  System.


#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct {
    int id;
    char name[50];
    int age;
    char gender[10];
    char disease[100];
} Patient;

typedef struct {
    int id;
    char name[50];
    char specialization[50];
    char availability[20];
} Doctor;
typedef struct {
    int id;
    int patientID;
    int doctorID;
    char date[20];
    char time[20];
} Appointment;

typedef struct {
    int id;
    char name[50];
    int stock;
    char expiry[20];
} Medicine;

typedef struct {
    int billID;
    int patientID;
    float doctorCharge;
    float medicineCharge;
    float roomCharge;
    float totalBill;
} Billing;

/***************************
   GLOBAL ARRAYS & COUNTERS
****************************/
Patient patients[100];
Doctor doctors[100];
Appointment appointments[100];
Medicine medicines[100];
Billing bills[100];

int pCount = 0, dCount = 0, aCount = 0, mCount = 0, bCount = 0;

/***************************
   FILE HANDLING FUNCTIONS
****************************/
void loadPatients() {
    FILE *fp = fopen("patient.txt", "r");
    if (!fp) return;
    while (fscanf(fp, "%d %s %d %s %s",
        &patients[pCount].id,
        patients[pCount].name,
        &patients[pCount].age,
        patients[pCount].gender,
        patients[pCount].disease) != EOF)
    { pCount++; }
    fclose(fp);
}

void savePatients() {
    FILE *fp = fopen("patient.txt", "w");
    for (int i = 0; i < pCount; i++) {
        fprintf(fp, "%d %s %d %s %s\n",
            patients[i].id,
            patients[i].name,
            patients[i].age,
            patients[i].gender,
            patients[i].disease);
    }
    fclose(fp);
}

void loadDoctors() {
    FILE *fp = fopen("doctor.txt", "r");
    if (!fp) return;
    while (fscanf(fp, "%d %s %s %s",
        &doctors[dCount].id,
        doctors[dCount].name,
        doctors[dCount].specialization,
        doctors[dCount].availability) != EOF)
    { dCount++; }
    fclose(fp);
}

void saveDoctors() {
    FILE *fp = fopen("doctor.txt", "w");
    for (int i = 0; i < dCount; i++) {
        fprintf(fp, "%d %s %s %s\n",
            doctors[i].id,
            doctors[i].name,
            doctors[i].specialization,
            doctors[i].availability);
    }
    fclose(fp);
}

void loadAppointments() {
    FILE *fp = fopen("appointment.txt", "r");
    if (!fp) return;
    while (fscanf(fp, "%d %d %d %s %s",
        &appointments[aCount].id,
        &appointments[aCount].patientID,
        &appointments[aCount].doctorID,
        appointments[aCount].date,
        appointments[aCount].time) != EOF)
    { aCount++; }
    fclose(fp);
}

void saveAppointments() {
    FILE *fp = fopen("appointment.txt", "w");
    for (int i = 0; i < aCount; i++) {
        fprintf(fp, "%d %d %d %s %s\n",
            appointments[i].id,
            appointments[i].patientID,
            appointments[i].doctorID,
            appointments[i].date,
            appointments[i].time);
    }
    fclose(fp);
}

void loadMedicines() {
    FILE *fp = fopen("medicine.txt", "r");
    if (!fp) return;
    while (fscanf(fp, "%d %s %d %s",
        &medicines[mCount].id,
        medicines[mCount].name,
        &medicines[mCount].stock,
        medicines[mCount].expiry) != EOF)
    { mCount++; }
    fclose(fp);
}

void saveMedicines() {
    FILE *fp = fopen("medicine.txt", "w");
    for (int i = 0; i < mCount; i++) {
        fprintf(fp, "%d %s %d %s\n",
            medicines[i].id,
            medicines[i].name,
            medicines[i].stock,
            medicines[i].expiry);
    }
    fclose(fp);
}

void loadBills() {
    FILE *fp = fopen("billing.txt", "r");
    if (!fp) return;
    while (fscanf(fp, "%d %d %f %f %f %f",
        &bills[bCount].billID,
        &bills[bCount].patientID,
        &bills[bCount].doctorCharge,
        &bills[bCount].medicineCharge,
        &bills[bCount].roomCharge,
        &bills[bCount].totalBill) != EOF)
    { bCount++; }
    fclose(fp);
}

void saveBills() {
    FILE *fp = fopen("billing.txt", "w");
    for (int i = 0; i < bCount; i++) {
        fprintf(fp, "%d %d %.2f %.2f %.2f %.2f\n",
            bills[i].billID,
            bills[i].patientID,
            bills[i].doctorCharge,
            bills[i].medicineCharge,
            bills[i].roomCharge,
            bills[i].totalBill);
    }
    fclose(fp);
}

/***************************
   PATIENT MANAGEMENT
****************************/
void addPatient() {
    Patient p;
    printf("\nEnter Patient ID: ");
    scanf("%d", &p.id);
    printf("Enter Name: ");
    scanf("%s", p.name);
    printf("Enter Age: ");
    scanf("%d", &p.age);
    printf("Enter Gender: ");
    scanf("%s", p.gender);
    printf("Enter Disease: ");
    scanf("%s", p.disease);

    patients[pCount++] = p;
    printf("\nPatient Added Successfully!\n");
}

void displayPatients() {
    printf("\n========== PATIENT LIST ==========\n");
    for (int i = 0; i < pCount; i++) {
        printf("\n----- PATIENT %d -----\n", i + 1);
        printf("Patient ID      : %d\n", patients[i].id);
        printf("Name            : %s\n", patients[i].name);
        printf("Age             : %d\n", patients[i].age);
        printf("Gender          : %s\n", patients[i].gender);
        printf("Disease         : %s\n", patients[i].disease);
    }
    printf("\n==================================\n");
}
void searchPatient() {
    int id;
    printf("\nEnter Patient ID to search: ");
    scanf("%d", &id);

    for (int i = 0; i < pCount; i++) {
        if (patients[i].id == id) {
            printf("\n===== PATIENT FOUND =====\n");
            printf("Patient ID      : %d\n", patients[i].id);
            printf("Name            : %s\n", patients[i].name);
            printf("Age             : %d\n", patients[i].age);
            printf("Gender          : %s\n", patients[i].gender);
            printf("Disease         : %s\n", patients[i].disease);
            return;
        }
    }

    printf("\nPatient with ID %d not found!\n", id);
}
void updatePatient() {
    int id;
    printf("\nEnter Patient ID to update: ");
    scanf("%d", &id);

    for (int i = 0; i < pCount; i++) {
        if (patients[i].id == id) {
            printf("\n===== UPDATE PATIENT INFORMATION =====\n");

            printf("Enter New Name: ");
            scanf("%s", patients[i].name);

            printf("Enter New Age: ");
            scanf("%d", &patients[i].age);

            printf("Enter New Gender: ");
            scanf("%s", patients[i].gender);

            printf("Enter New Disease: ");
            scanf("%s", patients[i].disease);

            printf("\nPatient Information Updated Successfully!\n");
            return;
        }
    }

    printf("\nPatient with ID %d not found!\n", id);
}

void deletePatient() {
    int id;
    printf("\nEnter Patient ID to delete: ");
    scanf("%d", &id);

    for (int i = 0; i < pCount; i++) { 
        if (patients[i].id == id) {

            // shift all records left
            for (int j = i; j < pCount - 1; j++) {
                patients[j] = patients[j + 1];
            }

            pCount--;
            printf("\nPatient Record Deleted Successfully!\n");
            return;
        }
    }

    printf("\nPatient with ID %d not found!\n", id);
}

/***************************
   DOCTOR MANAGEMENT
****************************/
void addDoctor() {
    Doctor d;
    printf("\nEnter Doctor ID: ");
    scanf("%d", &d.id);
    printf("Enter Name: ");
    scanf("%s", d.name);
    printf("Enter Specialization: ");
    scanf("%s", d.specialization);
    printf("Enter Availability: ");
    scanf("%s", d.availability);

    doctors[dCount++] = d;
    printf("\nDoctor Added Successfully!\n");
}

void displayDoctors() {
    printf("\n========== DOCTOR LIST ==========\n");
    for (int i = 0; i < dCount; i++) {
        printf("\n----- DOCTOR %d -----\n", i + 1);
        printf("Doctor ID       : %d\n", doctors[i].id);
        printf("Name            : %s\n", doctors[i].name);
        printf("Specialization  : %s\n", doctors[i].specialization);
        printf("Availability    : %s\n", doctors[i].availability);
    }
    printf("\n=================================\n");
}
void updateDoctor() {
    int id;
    printf("\nEnter Doctor ID to update: ");
    scanf("%d", &id);

    for (int i = 0; i < dCount; i++) {
        if (doctors[i].id == id) {

            printf("\n===== UPDATE DOCTOR DETAILS =====\n");

            printf("Enter New Name: ");
            scanf("%s", doctors[i].name);

            printf("Enter New Specialization: ");
            scanf("%s", doctors[i].specialization);

            printf("Enter New Availability: ");
            scanf("%s", doctors[i].availability);

            printf("\nDoctor Details Updated Successfully!\n");
            return;
        }
    }

    printf("\nDoctor with ID %d not found!\n", id);
}
void deleteDoctor() {
    int id;
    printf("\nEnter Doctor ID to delete: ");
    scanf("%d", &id);

    for (int i = 0; i < dCount; i++) {
        if (doctors[i].id == id) {

            // Shift elements left
            for (int j = i; j < dCount - 1; j++) {
                doctors[j] = doctors[j + 1];
            }

            dCount--;
            printf("\nDoctor Deleted Successfully!\n");
            return;
        }
    }

    printf("\nDoctor with ID %d not found!\n", id);
}
void assignSpecialization() {
    int id;
    printf("\nEnter Doctor ID to assign specialization: ");
    scanf("%d", &id);

    for (int i = 0; i < dCount; i++) {
        if (doctors[i].id == id) {

            printf("\nEnter New Specialization: ");
            scanf("%s", doctors[i].specialization);

            printf("\nSpecialization Updated Successfully!\n");
            return;
        }
    }

    printf("\nDoctor with ID %d not found!\n", id);
}

/***************************
   APPOINTMENT MODULE
****************************/
void bookAppointment() {
    Appointment a;
    printf("\nEnter Appointment ID: ");
    scanf("%d", &a.id);
    printf("Enter Patient ID: ");
    scanf("%d", &a.patientID);
    printf("Enter Doctor ID: ");
    scanf("%d", &a.doctorID);
    printf("Enter Date: ");
    scanf("%s", a.date);
    printf("Enter Time: ");
    scanf("%s", a.time);

    appointments[aCount++] = a;
    printf("\nAppointment Booked!\n");
}

void viewAppointments() {
    printf("\n========== APPOINTMENT LIST ==========\n");
    for (int i = 0; i < aCount; i++) {
        printf("\n----- APPOINTMENT %d -----\n", i + 1);
        printf("Appointment ID  : %d\n", appointments[i].id);
        printf("Patient ID      : %d\n", appointments[i].patientID);
        printf("Doctor ID       : %d\n", appointments[i].doctorID);
        printf("Date            : %s\n", appointments[i].date);
        printf("Time            : %s\n", appointments[i].time);
    }
    printf("\n======================================\n");
}
void updateAppointment() {
    int id;
    printf("\nEnter Appointment ID to update: ");
    scanf("%d", &id);

    for (int i = 0; i < aCount; i++) {
        if (appointments[i].id == id) {

            printf("\n===== UPDATE APPOINTMENT =====\n");

            printf("Enter New Patient ID: ");
            scanf("%d", &appointments[i].patientID);

            printf("Enter New Doctor ID: ");
            scanf("%d", &appointments[i].doctorID);

            printf("Enter New Date: ");
            scanf("%s", appointments[i].date);

            printf("Enter New Time: ");
            scanf("%s", appointments[i].time);

            printf("\nAppointment Updated Successfully!\n");
            return;
        }
    }

    printf("\nAppointment with ID %d not found!\n", id);
}
void cancelAppointment() {
    int id;
    printf("\nEnter Appointment ID to cancel: ");
    scanf("%d", &id);

    for (int i = 0; i < aCount; i++) {
        if (appointments[i].id == id) {

            for (int j = i; j < aCount - 1; j++) {
                appointments[j] = appointments[j + 1];
            }

            aCount--;
            printf("\nAppointment Cancelled Successfully!\n");
            return;
        }
    }

    printf("\nAppointment with ID %d not found!\n", id);
}
void checkDoctorAvailability() {
    int doctorID;
    char date[20], time[20];

    printf("\nEnter Doctor ID: ");
    scanf("%d", &doctorID);
    printf("Enter Date: ");
    scanf("%s", date);
    printf("Enter Time: ");
    scanf("%s", time);

    for (int i = 0; i < aCount; i++) {
        if (appointments[i].doctorID == doctorID &&
            strcmp(appointments[i].date, date) == 0 &&
            strcmp(appointments[i].time, time) == 0) {

            printf("\nDoctor is NOT Available at this time! Already booked.\n");
            return;
        }
    }

    printf("\nDoctor is Available.\n");
}


/***************************
   MEDICINE MODULE
****************************/
void addMedicine() {
    Medicine m;
    printf("\nEnter Medicine ID: ");
    scanf("%d", &m.id);
    printf("Enter Name: ");
    scanf("%s", m.name);
    printf("Enter Stock: ");
    scanf("%d", &m.stock);
    printf("Enter Expiry Date: ");
    scanf("%s", m.expiry);

    medicines[mCount++] = m;
    printf("\nMedicine Added Successfully!\n");
}

void displayMedicines() {
    printf("\n========== MEDICINE LIST ==========\n");
    for (int i = 0; i < mCount; i++) {
        printf("\n----- MEDICINE %d -----\n", i + 1);
        printf("Medicine ID     : %d\n", medicines[i].id);
        printf("Name            : %s\n", medicines[i].name);
        printf("Stock           : %d\n", medicines[i].stock);
        printf("Expiry Date     : %s\n", medicines[i].expiry);
    }
    printf("\n===================================\n");
}
void updateStock() {
    int id, newStock;
    printf("\nEnter Medicine ID to update stock: ");
    scanf("%d", &id);

    for (int i = 0; i < mCount; i++) {
        if (medicines[i].id == id) {

            printf("Enter New Stock Quantity: ");
            scanf("%d", &newStock);

            medicines[i].stock = newStock;

            printf("\nStock Updated Successfully!\n");
            return;
        }
    }

    printf("\nMedicine with ID %d not found!\n", id);
}
void issueMedicine() {
    int id, qty;

    printf("\nEnter Medicine ID to issue: ");
    scanf("%d", &id);

    for (int i = 0; i < mCount; i++) {
        if (medicines[i].id == id) {

            printf("Enter Quantity to Issue: ");
            scanf("%d", &qty);

            if (qty <= medicines[i].stock) {
                medicines[i].stock -= qty;
                printf("\nMedicine Issued Successfully!\n");
                printf("Remaining Stock: %d\n", medicines[i].stock);
            } else {
                printf("\nNot Enough Stock Available!\n");
            }
            return;
        }
    }

    printf("\nMedicine with ID %d not found!\n", id);
}
void showAlerts() {
    printf("\n========== ALERTS ==========\n");

    int alertFound = 0;

    for (int i = 0; i < mCount; i++) {

        // LOW STOCK ALERT
        if (medicines[i].stock < 10) {
            printf("\n? LOW STOCK ALERT\n");
            printf("Medicine: %s | Stock: %d\n",
                   medicines[i].name, medicines[i].stock);
            alertFound = 1;
        }

        // EXPIRY ALERT (simple demonstration)
        if (strcmp(medicines[i].expiry, "2025") < 0) { 
            printf("\n? EXPIRY ALERT\n");
            printf("Medicine: %s | Expiry: %s\n",
                   medicines[i].name, medicines[i].expiry);
            alertFound = 1;
        }
    }

    if (!alertFound) {
        printf("\nNo Alerts. All Medicines Normal.\n");
    }

    printf("\n============================\n");
}
void deleteMedicine() {
    int id;
    printf("\nEnter Medicine ID to delete: ");
    scanf("%d", &id);

    for (int i = 0; i < mCount; i++) {

        if (medicines[i].id == id) {

            // Shift all records left
            for (int j = i; j < mCount - 1; j++) {
                medicines[j] = medicines[j + 1];
            }

            mCount--;
            printf("\nMedicine Deleted Successfully!\n");
            return;
        }
    }

    printf("\nMedicine with ID %d not found!\n", id);
}



/***************************
   BILLING MODULE
****************************/
void generateBill() {
    Billing b;
    printf("\nEnter Bill ID: ");
    scanf("%d", &b.billID);
    printf("Enter Patient ID: ");
    scanf("%d", &b.patientID);
    printf("Enter Doctor Charge: ");
    scanf("%f", &b.doctorCharge);
    printf("Enter Medicine Charge: ");
    scanf("%f", &b.medicineCharge);
    printf("Enter Room Charge: ");
    scanf("%f", &b.roomCharge);

    b.totalBill = b.doctorCharge + b.medicineCharge + b.roomCharge;

    bills[bCount++] = b;

    printf("\nBill Generated Successfully!\n");
    printf("Total Amount: %.2f\n", b.totalBill);
}

void displayBills() {
    printf("\n========== BILL LIST ==========\n");
    for (int i = 0; i < bCount; i++) {
        printf("\n----- BILL %d -----\n", i + 1);
        printf("Bill ID         : %d\n", bills[i].billID);
        printf("Patient ID      : %d\n", bills[i].patientID);
        printf("Doctor Charge   : %.2f\n", bills[i].doctorCharge);
        printf("Medicine Charge : %.2f\n", bills[i].medicineCharge);
        printf("Room Charge     : %.2f\n", bills[i].roomCharge);
        printf("TOTAL BILL      : %.2f\n", bills[i].totalBill);
    }
    printf("\n================================\n");
}
void addServicesCharges() {
    int billID;
    printf("\nEnter Bill ID to add/update services: ");
    scanf("%d", &billID);

    for (int i = 0; i < bCount; i++) {
        if (bills[i].billID == billID) {

            printf("\n===== UPDATE SERVICES & CHARGES =====\n");

            printf("Enter Doctor Charge: ");
            scanf("%f", &bills[i].doctorCharge);

            printf("Enter Medicine Charge: ");
            scanf("%f", &bills[i].medicineCharge);

            printf("Enter Room Charge: ");
            scanf("%f", &bills[i].roomCharge);

            printf("\nCharges Updated Successfully!\n");
            return;
        }
    }

    printf("\nBill with ID %d not found!\n", billID);
}
void calculateTotalAmount() {
    int billID;
    printf("\nEnter Bill ID to calculate total amount: ");
    scanf("%d", &billID);

    for (int i = 0; i < bCount; i++) {
        if (bills[i].billID == billID) {

            bills[i].totalBill = bills[i].doctorCharge +
                                 bills[i].medicineCharge +
                                 bills[i].roomCharge;

            printf("\nTotal Amount for Bill ID %d: %.2f\n", bills[i].billID, bills[i].totalBill);
            return;
        }
    }

    printf("\nBill with ID %d not found!\n", billID);
}

/***************************
   MENUS
****************************/
void patientMenu() {
    int choice;
    do {
        printf("\n========= Patient Menu =========\n");
        printf("1. Add Patient\n");
        printf("2. Display Patients\n");
        printf("3. Search Patient\n");
        printf("4. Update Patient\n");
        printf("5. Delete Patient\n");
        printf("0. Back\n");
        printf("================================\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1:
                addPatient();
                break;

            case 2:
                displayPatients();
                break;

            case 3:
                searchPatient();
                break;

            case 4:
                updatePatient();
                break;

            case 5:
                deletePatient();
                break;

            case 0:
                printf("Returning to Main Menu...\n");
                break;

            default:
                printf("Invalid choice! Please try again.\n");
        }

    } while (choice != 0);
}

void doctorMenu() {
    int choice;
    do {
        printf("\n========= Doctor Menu =========\n");
        printf("1. Add Doctor\n");
        printf("2. Display Doctors\n");
        printf("3. Update Doctor Details\n");
        printf("4. Delete Doctor\n");
        printf("5. Assign Specialization\n");
        printf("0. Back\n");
        printf("================================\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1:
                addDoctor();
                break;

            case 2:
                displayDoctors();
                break;

            case 3:
                updateDoctor();
                break;

            case 4:
                deleteDoctor();
                break;

            case 5:
                assignSpecialization();
                break;

            case 0:
                printf("Returning to Main Menu...\n");
                break;

            default:
                printf("Invalid choice! Please try again.\n");
        }

    } while (choice != 0);
}

void appointmentMenu() {
    int choice;
    do {
        printf("\n========= Appointment Menu =========\n");
        printf("1. Book Appointment\n");
        printf("2. View Appointments\n");
        printf("3. Update Appointment\n");
        printf("4. Cancel Appointment\n");
        printf("5. Check Doctor Availability\n");
        printf("0. Back\n");
        printf("====================================\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1:
                bookAppointment();
                break;

            case 2:
                viewAppointments();
                break;

            case 3:
                updateAppointment();
                break;

            case 4:
                cancelAppointment();
                break;

            case 5:
                checkDoctorAvailability();
                break;

            case 0:
                printf("Returning to Main Menu...\n");
                break;

            default:
                printf("Invalid choice! Try again.\n");
        }

    } while (choice != 0);
}

void medicineMenu() {
    int choice;
    do {
        printf("\n========= Medicine Menu =========\n");
        printf("1. Add Medicine\n");
        printf("2. Display Medicines\n");
        printf("3. Update Stock\n");
        printf("4. Issue Medicine to Patient\n");
        printf("5. Show Low-Stock & Expiry Alerts\n");
        printf("6. Delete Medicine\n");
        printf("0. Back\n");
        printf("=================================\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1:
                addMedicine();
                break;

            case 2:
                displayMedicines();
                break;

            case 3:
                updateStock();
                break;

            case 4:
                issueMedicine();
                break;

            case 5:
                showAlerts();
                break;

            case 6:
                deleteMedicine();
                break;

            case 0:
                printf("Returning to Main Menu...\n");
                break;

            default:
                printf("Invalid choice! Please try again.\n");
        }

    } while (choice != 0);
}

void billingMenu() {
    int choice;
    do {
        printf("\n========= Billing Menu =========\n");
        printf("1. Generate Bill\n");
        printf("2. Display Bills\n");
        printf("3. Add Services & Charges\n");
        printf("4. Calculate Total Amount\n");
        printf("0. Back\n");
        printf("================================\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1:
                generateBill();
                break;

            case 2:
                displayBills();
                break;

            case 3:
                addServicesCharges();
                break;

            case 4:
                calculateTotalAmount();
                break;

            case 0:
                printf("Returning to Main Menu...\n");
                break;

            default:
                printf("Invalid choice! Please try again.\n");
        }

    } while (choice != 0);
}


/***************************
        MAIN FUNCTION
****************************/
int main() {
    loadPatients();
    loadDoctors();
    loadAppointments();
    loadMedicines();
    loadBills();
    
 printf("_____________________________________________________________________________________\n\n");
 printf("Program Name   : Hospital Management System\n");
 printf("Language       : C\n");
 printf("Developer Name : Ahsan(64),noman(78),zeshan(13),Aatif(35),Mahnoor(30),Bisma(72)\n");
 printf("Class          : BS(Ai) / 1st Semester\n");
 printf("Institute      : QUAID-E-AWAM UNIVERSITY OF ENGINEERING,SCIENCE & TECHNOLOGY\n");
 printf("Description    : This program manages Doctor,patient,Appointment,Pharmacy records, billing, and reports.\n");
 printf("_____________________________________________________________________________________\n\n");
                  


    int choice;
    while (1) {
        printf("\n************** HOSPITAL MANAGEMENT SYSTEM ********************\n");
        printf("1. Patient Management\n");
        printf("2. Doctor Management\n");
        printf("3. Appointment System\n");
        printf("4. Medicine / Pharmacy\n");
        printf("5. Billing System\n");
        printf("0. Exit\n");
        printf("**************************************************************\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1: patientMenu(); break;
            case 2: doctorMenu(); break;
            case 3: appointmentMenu(); break;
            case 4: medicineMenu(); break;
            case 5: billingMenu(); break;
            case 0:
                savePatients();
                saveDoctors();
                saveAppointments();
                saveMedicines();
                saveBills();
                printf("Data Saved! Exiting...\n");
                exit(0);
            default:
                printf("Invalid choice! Try again.\n");
        }
    }

    return 0;
}    
