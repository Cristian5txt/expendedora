#include <iostream>
using namespace std;

void IngresarCristian(float &agua, float &chocolates, float &chicles);
void mostrarCristian(float &agua, float &chocolates, float &chicles, const float &preci1, const float &preci2, const float &preci3);
void comprarCristian(float &agua, float &chocolates, float &chicles, const float &preci1, const float &preci2, const float &preci3, float &dinero, float &saldoTotal);
void mostrarSaldoTotal(float saldoTotal);

int main() {
    float agua, chocolates, chicles;
    const float preci1 = 1.50;
    const float preci2 = 0.75;
    const float preci3 = 0.50;
    float dinero;
    int opcion;
    float saldoTotal = 0.0;
    IngresarCristian(agua, chocolates, chicles);

    do {
        cout << "--- Menu Principal ---" << endl;
        cout << "1. Mostrar productos" << endl;
        cout << "2. Comprar productos" << endl;
        cout << "3. Saldo de la maquina" << endl;
        cout << "0. Salir" << endl;
        cout << "Selecciona una opcion: "<<endl;
        cin >> opcion;

        switch (opcion) {
            case 1:
                mostrarCristian(agua, chocolates, chicles, preci1, preci2, preci3);
                break;
            case 2:
                cout << "Ingresa la cantidad de dinero disponible: $";
                cin >> dinero;
                comprarCristian(agua, chocolates, chicles, preci1, preci2, preci3, dinero, saldoTotal);
                break;
            case 3:
                mostrarSaldoTotal(saldoTotal);
                break;
            case 0:
                cout << "Gracias por comprar" << endl;
                break;
            default:
                cout << "Intenta de nuevo" << endl;
                break;
        }
    } while (opcion != 0);

    return 0;
}


void IngresarCristian(float &agua, float &chocolates, float &chicles) {
    cout << "INGRESE LA CANTIDAD DE AGUAS QUE HAY: "<<endl;
    cin >> agua;
    cout << "INGRESE LA CANTIDAD DE CHOCOLATES QUE HAY: "<<endl;
    cin >> chocolates;
    cout << "INGRESE LA CANTIDAD DE CHICLES QUE HAY: "<<endl;
    cin >> chicles;
}


void mostrarCristian(float &agua, float &chocolates, float &chicles, const float &preci1, const float &preci2, const float &preci3) {
    cout << "______________________________" << endl;
    cout << "|CANTIDAD |" << " PRODUCTO |" << " PRECIO |" << endl;
    cout << "|-----------------------------|" << endl;
    cout << "|   " << agua << "    |" << "   AGUAS  |" << "  $" << preci1 << "  |" << endl;
    cout << "|-----------------------------|" << endl;
    cout << "|   " << chocolates << "    |" << "Chocolates|" << " $" << preci2 << "  |" << endl;
    cout << "|-----------------------------|" << endl;
    cout << "|   " << chicles << "    |" << " Chicles  |" << " $" << preci3 << "   |" << endl;
    cout << "------------------------------" << endl;
}

void comprarCristian(float &agua, float &chocolates, float &chicles, const float &preci1, const float &preci2, const float &preci3, float &dinero, float &saldoTotal) {
    int opcionProducto;
    cout << "---- PRODUCTOS DISPONIBLES ----" << endl;
    cout << "1. Agua ($" << preci1 << ")" << endl;
    cout << "2. Chocolates ($" << preci2 << ")" << endl;
    cout << "3. Chicles ($" << preci3 << ")" << endl;
    cout << "0. Cancelar" << endl;
    cout << "Selecciona el producto que deseas comprar: "<<endl;
    cin >> opcionProducto;

    switch (opcionProducto) {
        case 1:
            if (agua > 0 && dinero >= preci1) {
                agua--;
                dinero =dinero-preci1;
                saldoTotal =saldoTotal+preci1;
                cout << "Has comprado un Agua su dinero restante: $" << dinero << endl;
            } else if (agua <= 0) {
                cout << "No hay Agua disponible" << endl;
            } else {
                cout << "Dinero insuficiente para comprar Agua" << endl;
            }
            break;
        case 2:
            if (chocolates > 0 && dinero >= preci2) {
                chocolates--;
                dinero =dinero-preci2;
                saldoTotal =saldoTotal+preci2;
                cout << "Has comprado un Chocolate su dinero restante: $" << dinero << endl;
            } else if (chocolates <= 0) {
                cout << "No hay Chocolates disponibles" << endl;
            } else {
                cout << "Dinero insuficiente para comprar Chocolates" << endl;
            }
            break;
        case 3:
            if (chicles > 0 && dinero >= preci3) {
                chicles--;
                dinero =dinero-preci3;
                saldoTotal =saldoTotal+preci3;
                cout << "Has comprado un Chicle su dinero restante: $" << dinero << endl;
            } else if (chicles <= 0) {
                cout << "No hay Chicles disponibles." << endl;
            } else {
                cout << "Dinero insuficiente para comprar Chicles" << endl;
            }
            break;
        case 0:
            cout << "Compra cancelada" << endl;
            break;
        default:
            cout << "Intenta de nuevo" << endl;
            break;
    }
}

void mostrarSaldoTotal(float saldoTotal) {
    cout << "EL VALOR TOTAL ES: $" << saldoTotal << endl;
}
