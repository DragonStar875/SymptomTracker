#include <iostream>
#include <time.h>
#include <vector>
using namespace std;

class People{
    //general patient info
    struct Patient{
        int fever;
        int cough;
        int shortBreath;
        int runnyNose;
        int headache;
        int sneezing;
        int fatigue;
    }person;

    public:
    vector<Patient> Patients;
    //randomly assigns 0 or 1 to each symptom
    void getSypmptoms(int numPatients){
        srand(time(0));

        for(int i = 0; i < numPatients; ++i){
            person.fever = rand() % 2;
            person.cough = rand() % 2;
            person.shortBreath = rand() % 2;
            person.runnyNose = rand() % 2;
            person.headache = rand() % 2;
            person.sneezing = rand() % 2;
            person.fatigue = rand() % 2;
            Patients.push_back(person);
        }
    }
}people;

class Doctor: public People{
    float covid;
    float cold;
    float flu;
    float other;

    int percentCovid;
    int percentCold;
    int percentFlu;
    int percentOther;

    //determines what illness a pacient has based on the 0 or 1
    void findIllnesses(int numPatients){
        for(int i = 0; i < numPatients; ++i){
            if(people.Patients[i].fever == 1 &&
               people.Patients[i].cough == 1 &&
               people.Patients[i].shortBreath == 1 &&
               people.Patients[i].sneezing == 0){
                covid += 1;
            }else{
                if(people.Patients[i].shortBreath == 0 &&
                   people.Patients[i].runnyNose == 1 &&
                   people.Patients[i].sneezing == 1){
                    cold += 1;
                }else{
                    if(people.Patients[i].fever == 1 &&
                       people.Patients[i].cough == 1 &&
                       people.Patients[i].shortBreath == 0 &&
                       people.Patients[i].headache == 1 &&
                       people.Patients[i].sneezing == 0 &&
                       people.Patients[i].fatigue == 1){
                        flu += 1;
                    }else{
                        other += 1;
                    }
                }
            }
        }
    }

    public:
    void printData(int numPatients){
        findIllnesses(numPatients);

        //prints the stats of each illness
        cout << "=======================================\n"
                "Symptoms Checker...\n"
                << covid << " Patients have symptoms of COVID-19\n"
                << cold << " Patients have symptoms of the cold\n"
                << flu << " Patients have sympotoms of the flu\n"
                << other << " Patients have some other illness\n"
                "=======================================\n\n";

        //converts the stats into percentages
        percentCovid = (covid / numPatients) * 100;
        percentCold = (cold / numPatients) * 100;
        percentFlu = (flu / numPatients) * 100;
        percentOther = (other / numPatients) * 100;
        
        //shows the percentage of each illness with plus sings
        cout << "Percentage of each illness:\n"
                "COVID-19:        [" << percentCovid << "%]";
        for(int i = 0; i < percentCovid; ++i){
            cout << "+";
        }

        cout << "\nCold:            [" << percentCold << "%]";
        for(int i = 0; i < percentCold; ++i){
            cout << "+";
        }

        cout << "\nFlu:             [" << percentFlu << "%]";
        for(int i = 0; i < percentFlu; ++i){
            cout << "+";
        }

        cout << "\nOther Ilnness:   [" << percentOther << "%]";
        for(int i = 0; i < percentOther; ++i){
            cout << "+";
        }
    }
}doctor;

int main(){
    int numPatients;

    //shows the list of illnesses and their symptomms
    cout << "Welcome to Symptoms Checker\n\n"
            "Guide: * Common       + Sometimes/Rarely       - NO\n"
            "===================================================\n"
            "Symptoms            |  COVID-19  |  Cold  |  Flu  |\n"
            "===================================================\n"
            "Fever               |      *     |    +   |   *   |\n"
            "Cough               |      *     |    +   |   *   |\n"
            "Shortness of Breath |      *     |    -   |   -   |\n"
            "Runny Nose          |      +     |    *   |   +   |\n"
            "Headaches           |      +     |    +   |   *   |\n"
            "Sneezing            |      -     |    *   |   -   |\n"
            "Fatigue             |      +     |    +   |   *   |\n"
            "===================================================\n\n"
            "Please enter how many patients you have: ";

    //verifies their input
    while(!(cin >> numPatients)){
        cout << "Invalid input. Please enter a valid number.\n";
        cin.clear();
        cin.ignore(256, '\n');
        cout << "Please enter how many patients you have: ";
    }

    //does all the math and calculations
    people.getSypmptoms(numPatients);
    cout << "\n";
    doctor.printData(numPatients);
}
