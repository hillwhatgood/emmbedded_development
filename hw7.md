1. Make "hw7" directory and create C++ program files named as before: like p1.cpp
2. problems

    Listing 6-14 program can be used to communicate to the AM230x/DHT family of sensors to get temperature and humidity. For human beings, there is another kind of temperature: felt air temperature. Can you compute it based on the acquired temperature and humidity from the  AM230x/DHT sensor and show them?     
You can program based on Listing 6-14, but you need to compare your results with the ones from Central Weather Bureau.

    For the computation of felt air temperature, you can reference 'Robert G. Steadman, A universal scale of apparent temperature'. The equation is as follows:

<img src="imgs/air_temperature.jpg" alt="felt air temperature">
#include <iostream>
#include <cmath> // For math functions

// Function to compute the felt air temperature (apparent temperature)
double computeFeltAirTemperature(double temperature, double humidity) {
    // Constants for the Steadman formula
    const double a = 17.27;
    const double b = 237.7;
    
    // Base of the natural logarithm
    double lv = std::log((humidity / 100.0) * std::exp((a * temperature) / (b + temperature)) + 1.0);
    
    // Steadman's formula to calculate the felt air temperature
    double T = (b * lv) / (a - lv) - 273.15; // Convert to Celsius
    
    return T;
}

int main() {
    // Variables to store temperature and humidity
    double temperature, humidity;
    
    // Assume these values are read from the AM230x/DHT sensor
    std::cout << "Enter the temperature (Celsius): ";
    std::cin >> temperature;
    std::cout << "Enter the humidity (%): ";
    std::cin >> humidity;
    
    // Compute the felt air temperature
    double feltTemperature = computeFeltAirTemperature(temperature, humidity);
    
    // Output the results
    std::cout << "The felt air temperature is: " << feltTemperature << " degrees Celsius" << std::endl;
    
    return 0;
}
