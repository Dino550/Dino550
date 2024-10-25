#include<iostream>
#include <cmath>
#define PI 3.1416

using namespace std;

int main(){
	
	float V_rot[3];  
	double V1[3];    
	double k[3];     
	double Producto_Punto;
	double Producto_Cruz[3]; 
	double a = 0;       
	
	
	cout << "Ingrese los valores del Vector 1: " << endl;
	cout << "x: ";
	cin >> V1[0];
	cout << "y: ";
	cin >> V1[1];
	cout << "z: ";
	cin >> V1[2];
	
	
	cout << "Ingrese el valor del angulo en grados: ";
	cin >> a;
	double rad = a*PI/180;
	
	
	k[0] = 0;
	k[1] = 0;
	k[2] = 1;
	
	// Calcular el producto cruz k x V1
	Producto_Cruz[0] = k[1] * V1[2] - k[2] * V1[1];
	Producto_Cruz[1] = k[2] * V1[0] - k[0] * V1[2];
	Producto_Cruz[2] = k[0] * V1[1] - k[1] * V1[0];
	
	// Calcular el producto punto k · V1
	Producto_Punto = V1[0] * k[0] + V1[1] * k[1] + V1[2] * k[2];
	
	// Fórmula de rotación de Rodrigues
	V_rot[0] = V1[0] * cos(rad) + Producto_Cruz[0] * sin(rad) + k[0] * (Producto_Punto * (1 - cos(rad)));
	V_rot[1] = V1[1] * cos(rad) + Producto_Cruz[1] * sin(rad) + k[1] * (Producto_Punto * (1 - cos(rad)));
	V_rot[2] = V1[2] * cos(rad) + Producto_Cruz[2] * sin(rad) + k[2] * (Producto_Punto * (1 - cos(rad)));


	cout << "Vector rotado: (" << V_rot[0] << ", " << V_rot[1] << ", " << V_rot[2] << ")" << endl;
	
	return 0;
}

