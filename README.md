# demo
import java.util.Scanner;

public class UnitConversionApp {

    // Conversion methods
    public static double convertLength(double value, String fromUnit, String toUnit) {
        // Convert everything to meters first
        switch (fromUnit.toLowerCase()) {
            case "meters":
                break;
            case "kilometers":
                value *= 1000;
                break;
            case "miles":
                value *= 1609.34;
                break;
            case "yards":
                value *= 0.9144;
                break;
            case "feet":
                value *= 0.3048;
                break;
            case "inches":
                value *= 0.0254;
                break;
            default:
                System.out.println("Invalid from unit.");
                return -1;
        }
        // Convert from meters to target unit
        switch (toUnit.toLowerCase()) {
            case "meters":
                break;
            case "kilometers":
                value /= 1000;
                break;
            case "miles":
                value /= 1609.34;
                break;
            case "yards":
                value /= 0.9144;
                break;
            case "feet":
                value /= 0.3048;
                break;
            case "inches":
                value /= 0.0254;
                break;
            default:
                System.out.println("Invalid to unit.");
                return -1;
        }
        return value;
    }

    public static double convertWeight(double value, String fromUnit, String toUnit) {
        // Convert everything to grams first
        switch (fromUnit.toLowerCase()) {
            case "grams":
                break;
            case "kilograms":
                value *= 1000;
                break;
            case "pounds":
                value *= 453.592;
                break;
            case "ounces":
                value *= 28.3495;
                break;
            default:
                System.out.println("Invalid from unit.");
                return -1;
        }
        // Convert from grams to target unit
        switch (toUnit.toLowerCase()) {
            case "grams":
                break;
            case "kilograms":
                value /= 1000;
                break;
            case "pounds":
                value /= 453.592;
                break;
            case "ounces":
                value /= 28.3495;
                break;
            default:
                System.out.println("Invalid to unit.");
                return -1;
        }
        return value;
    }

    public static double convertTemperature(double value, String fromUnit, String toUnit) {
        switch (fromUnit.toLowerCase()) {
            case "celsius":
                if (toUnit.equalsIgnoreCase("fahrenheit")) {
                    return (value * 9/5) + 32;
                } else if (toUnit.equalsIgnoreCase("kelvin")) {
                    return value + 273.15;
                }
                break;
            case "fahrenheit":
                if (toUnit.equalsIgnoreCase("celsius")) {
                    return (value - 32) * 5/9;
                } else if (toUnit.equalsIgnoreCase("kelvin")) {
                    return ((value - 32) * 5/9) + 273.15;
                }
                break;
            case "kelvin":
                if (toUnit.equalsIgnoreCase("celsius")) {
                    return value - 273.15;
                } else if (toUnit.equalsIgnoreCase("fahrenheit")) {
                    return ((value - 273.15) * 9/5) + 32;
                }
                break;
            default:
                System.out.println("Invalid from unit.");
                return -1;
        }
        System.out.println("Invalid to unit.");
        return -1;
    }

    // Main method
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Unit Conversion App");
        System.out.println("Choose the type of conversion:");
        System.out.println("1. Length");
        System.out.println("2. Weight");
        System.out.println("3. Temperature");
        int choice = scanner.nextInt();

        System.out.println("Enter the value to convert:");
        double value = scanner.nextDouble();

        System.out.println("Enter the from unit:");
        String fromUnit = scanner.next();

        System.out.println("Enter the to unit:");
        String toUnit = scanner.next();

        double result = -1;
        switch (choice) {
            case 1:
                result = convertLength(value, fromUnit, toUnit);
                break;
            case 2:
                result = convertWeight(value, fromUnit, toUnit);
                break;
            case 3:
                result = convertTemperature(value, fromUnit, toUnit);
                break;
            default:
                System.out.println("Invalid choice.");
                break;
        }

        if (result != -1) {
            System.out.printf("Converted value: %.2f %s\n", result, toUnit);
        }
    }
}
