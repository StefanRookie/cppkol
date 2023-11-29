
1.Reliazovati klasu " KompleksanBroj koja sadrzi privatne podatke članove imag i real, kao i javne članove: statički podatak
clan broj_objekata, konstruktor bez.argumenata (inkrementira broj _objekata),konstruktor koji inicializuje objeka klase TRompleksanBroj
(inkrementira brojobjekata)., konstruktor kopije (inkrementira broj objckala), destruktor (dekremetnira broj_objckata), kao i funkciju koja
računa meduo kompleksnog broja. U okviru funkcije main:
dinamički kreirati objekat klase TKompleksanBroj, inicijalizovati ga sa (1. 0, 2.0) injegovu adresu upisati u pokazivač
p koji pokazuje na klasu TKompleksanBroj,
ispisatì vrijednost modula kompleksnog broja na koji pokuguje pokazivač p, i ispisati vrijcdnost upisanu u staticki podatak Član
broj_objekata

#include <iostream>
#include <cmath>
using namespace std;

class TKompleksanBroj {
private:
    double real;
    double imag;
    
public:
    // Javni član za broj objekata
    static int broj_objekata;

    // Konstruktori
    TKompleksanBroj() {
        broj_objekata++;
    }

    TKompleksanBroj(double real, double imag) : real(real), imag(imag) {
        broj_objekata++;
    }

    TKompleksanBroj(const TKompleksanBroj& other) : real(other.real), imag(other.imag) {
        broj_objekata++;
    }

    // Destruktor
    ~TKompleksanBroj() {
        broj_objekata--;
    }

    // Funkcija za računanje modula kompleksnog broja
    double moduo() {
        return sqrt(real * real + imag * imag);
    }

    // Getteri
    double getReal() {
        return real;
    }

    double getImag() {
        return imag;
    }
};

// Inicijalizacija javnog člana broj_objekata
int TKompleksanBroj::broj_objekata = 0;

int main() {
    // Dinamičko kreiranje objekta klase TKompleksanBroj 
    //TKompleksanBroj* p = new TKompleksanBroj(1.0,2.0); kad se radi sa pokazivacem
    TKompleksanBroj p(1.0, 2.0);
    
    // Ispisivanje vrijednosti modula kompleksnog broja
    cout << "Moduo kompleksnog broja: " << p.moduo() << endl; // p->modu() kad se radi sa pokazivacem

    // Ispisivanje vrijednosti javnog člana broj_objekata
    cout << "Broj objekata: " << p.broj_objekata << endl;// p->modu() kad se radi sa pokazivacem

    // Oslobađanje zauzetih resursa (dealokacija objekta)
    // delete p; kad se radi sa pokazivacem

    return 0;
}




2.Reliazovati klasu T3DVektor koja sadrzi private podatke lanove x, y i z, kao i javne clanove: konstruktor bez argumenata,
konstruktor koji inicijalizuje objekat klase T3DVektor, konstruktor kopije, destruktor, funkciju Intezitet, kao i operatorske funkcije Clanice operator+= ioperator (vektorski proizvod).

U okviru funkcije main deklarisati objekat a klase T3DVektor i inicijalizovati ga sa (3.0, 4. 0, 5. 0), deklarisati objekat b na osnovu objekta a,
deklarisati objekat c koji dobija vrijednost a *b i ispisati njegov intezitet, 
deklarisati objekat d na osnovu objekta b, izvisiti naredbu d+-b; i ispisati intezitet vektora d.



#include <iostream>
#include <cmath>

class T3DVektor {
private:
    double x;
    double y;
    double z;

public:
    // Konstruktori
    T3DVektor() : x(0.0), y(0.0), z(0.0) {}

    T3DVektor(double x, double y, double z) : x(x), y(y), z(z) {}

    T3DVektor(const T3DVektor& other) : x(other.x), y(other.y), z(other.z) {}

    // Destruktor
    ~T3DVektor() {}

    // Funkcija za izračunavanje intenziteta
    double Intenzitet() const {
        return sqrt(x * x + y * y + z * z);
    }

    // Operatorske funkcije članice
    T3DVektor& operator+=(const T3DVektor& other) {
        x += other.x;
        y += other.y;
        z += other.z;
        return *this;
    }

    T3DVektor operator*(const T3DVektor& other) const {
        // Vektorski proizvod
        double resultX = y * other.z - z * other.y;
        double resultY = z * other.x - x * other.z;
        double resultZ = x * other.y - y * other.x;

        return T3DVektor(resultX, resultY, resultZ);
    }

};

int main() {
    // Inicijalizacija vektora a
    T3DVektor a(3.0, 4.0, 5.0);

    // Inicijalizacija vektora b na osnovu vektora a
    T3DVektor b(a);

    // Inicijalizacija vektora c koji dobija vrednost a * b
    T3DVektor c = a * b;

    // Ispisivanje intenziteta vektora c
    std::cout << "Intenzitet vektora c: " << c.Intenzitet() << std::endl;

    // Inicijalizacija vektora d na osnovu vektora b
    T3DVektor d(b);

    // Oduzimanje vektora b od vektora d
    d += b;

    // Ispisivanje intenziteta vektora d
    std::cout << "Intenzitet vektora d: " << d.Intenzitet() << std::endl;

    return 0;
}
