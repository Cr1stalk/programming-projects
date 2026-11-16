
#include <iostream>
#include <iomanip>
#include <sstream>
#include <string>
#include <stdexcept>
using namespace std;

const double a = -0.2;
const double b = 0.2;

/**
 * Calculates the sum of the series.
 * The first term satisfying |u| < eps is included.
 * Requires |x| <= 0.2 and eps > 0.
 * The function does not validate its arguments.
 * @param x The argument of the series.
 * @param eps The calculation accuracy.
 * @return The calculated sum.
 */
double s(double x, double eps)
{
    double u = x;
    double sum = 0.0;
    double k = 2.0;
    double twoX = 2.0 * x;
    while (u >= eps || u <= -eps)
    {
        sum += u;
        u *= twoX * (2.0 * k - 1.0) * (k - 1.0)
            / (k * k);
        k++;
    }
    sum += u;
    return sum;
}

/**
 * Reads one double value from cin.
 * @param field The name of the input field.
 * @return The entered number.
 * @throws invalid_argument If the input is incorrect.
 */
double readDouble(const string& field)
{
    string line;
    double value;

    if (!getline(cin, line))
        throw invalid_argument("Invalid " + field + ": input error.");

    istringstream iss(line);
    string extra;

    if (!(iss >> value) || (iss >> extra))
        throw invalid_argument(
            "Invalid " + field + ": expected one number."
        );
    return value;
}

/**
 * Reads and validates x.
 * @return A valid argument.
 * @throws invalid_argument If x is invalid.
 */
double inputX()
{
    double x = readDouble("x");

    if (!(x >= a && x <= b))
    {
        ostringstream message;
        message << "Invalid x: value must be in ["
            << a << "; " << b << "].";

        throw invalid_argument(message.str());
    }
    return x;
}

/**
 * Reads and validates eps.
 * @return A positive accuracy value.
 * @throws invalid_argument If eps is invalid.
 */
double inputEps()
{
    double eps = readDouble("eps");

    if (!(eps > 0))
        throw invalid_argument(
            "Invalid eps: value must be positive."
        );
    return eps;
}

int main()
{
    try
    {
        cout << "Lab work 2, variant 178" << "\n";
        cout << "Performer: Popeliar Mykyta" << "\n";
        cout << "Calculate the sum of a series." << "\n";

        cout << "Enter x (from " << a << " to " << b << "): ";
        double x = inputX();

        cout << "Enter eps (> 0): ";
        double eps = inputEps();

        cout << "\n***** do calculations ...";

        double result = s(x, eps);

        cout << " done" << "\n";

        cout << uppercase << scientific;
        cout << setprecision(7);
        cout << "for x = " << x << "\n";

        cout << setprecision(9);
        cout << "for eps = " << eps << "\n";

        cout << fixed << setprecision(8);
        cout << "result = " << result << "\n";
    }
    catch (const exception& e)
    {
        cout << "\n***** error" << "\n";
        cout << e.what() << "\n";
    }
}
