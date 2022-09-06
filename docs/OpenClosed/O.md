# Open Closed Principle
* Herhangi bir işlevsel kod bloğu yaptığı iş yetersiz kalınca yeni eklenecek özellikler için mevcut yapıyı koruyarak düzenleme yapılmalıdır.

## Mevcut durum
```java
class Vehicle{
	void start();
}
class Engine{
	Vehicle vehicle;
	void startEngine(){
		vehicle.start();
	}
	setVehicle(Vehicle vehicle);
}
```
**Yeni Araç Eklenmek İsteniyor**
```java
class Airplane{
}
```
## Hatalı Örnek
```java

class Vehicle{
	void start(){
		//Vehicle start
	}
}
class Airplane extends Vehicle{
	@Override
	void start(){
		//Airplane start
	}
}
class Engine{
	Vehicle vehicle;
	void startEngine(){
		vehicle.start();
	}
	setVehicle(Vehicle vehicle);
}
```
**Genişletilmeye açık olduğu için "Open" bölümünü sağlar fakat "start" methodu modifikasyona kapalı olmadığı için "Closed" bölümünü sağlamaz. İleride beklenmeyen sonuçlara yol açabilir.**
## Düzeltilmiş Örnek
```java

class Vehicle{
	//Final ile prensibin "Closed" kısmını sağladık
	final void start(){
		vehicleStart();
	}
	void vehicleStart(){
		//Start vehicle
	}
}
class Airplane extends Vehicle{
	//Start methodu Override edilemez
	//Eklenti yapılarak prensibin "Open" kısmı sağlandı
	void vehicleStart(){
		//Start airplane
	}
}
class Engine{
	Vehicle vehicle;
	void startEngine(){
		vehicle.start();
	}
	setVehicle(Vehicle vehicle);
}
```
