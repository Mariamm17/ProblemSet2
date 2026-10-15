# ProblemSet2

package edu.monmouth.problemSet2;

import edu.monmouth.campusvehicle.CampusVehicle;

public class ProblemSet2 {

    public static void main(String[] args) {

        System.out.println("PROBLEM SET 2");
        System.out.println("CAMPUS VEHICLE TESTING");

        // Requirements 8(b)-8(f): Default constructor and mutators
        System.out.println("\nTEST 1: DEFAULT CONSTRUCTOR");

        CampusVehicle vehicle1 = new CampusVehicle();

        // Requirement 8(c): Print default attributes
        printAttributes(vehicle1);

        // Requirement 8(d): Set valid attributes
        vehicle1.setId("MU1234");
        vehicle1.setLocation("Library");
        vehicle1.setAvailable(true);

        // Requirement 8(e): Print updated attributes
        printAttributes(vehicle1);

        // Requirement 8(f): Test checkout and return
        testCheckoutReturn(vehicle1);


        // Requirements 8(g)-8(k): Parameterized constructor
        System.out.println("\nTEST 2: PARAMETERIZED CONSTRUCTOR");

        CampusVehicle vehicle2 =
                new CampusVehicle("MU2026", "University Bluffs", false);

        // Requirement 8(h): Print initial attributes
        printAttributes(vehicle2);

        // Requirement 8(i): Change attributes
        vehicle2.setId("MU1090");
        vehicle2.setLocation("library");
        vehicle2.setAvailable(true);

        // Requirement 8(j): Print updated attributes
        printAttributes(vehicle2);

        // Requirement 8(k): Test checkout and return
        testCheckoutReturn(vehicle2);


        // Requirement 8(l): Test invalid IDs and locations
        System.out.println("\nTEST 3: NULL ID");
        CampusVehicle vehicle3 =
                new CampusVehicle(null, "Library", true);
        runTest(vehicle3);

        System.out.println("\nTEST 4: EMPTY ID");
        CampusVehicle vehicle4 =
                new CampusVehicle("", "Parking Lot", true);
        runTest(vehicle4);

        System.out.println("\nTEST 5: SHORT ID");
        CampusVehicle vehicle5 =
                new CampusVehicle("MU1", "Spruce Hall", false);
        runTest(vehicle5);

        System.out.println("\nTEST 6: LONG ID");
        CampusVehicle vehicle6 =
                new CampusVehicle("MU12345678901", "Laurel Hall", true);
        runTest(vehicle6);

        System.out.println("\nTEST 7: INVALID ID PREFIX");
        CampusVehicle vehicle7 =
                new CampusVehicle("AB1234", "University Bluffs", true);
        runTest(vehicle7);

        System.out.println("\nTEST 8: NULL LOCATION");
        CampusVehicle vehicle8 =
                new CampusVehicle("MU2001", null, true);
        runTest(vehicle8);

        System.out.println("\nTEST 9: EMPTY LOCATION");
        CampusVehicle vehicle9 =
                new CampusVehicle("MU2002", "", true);
        runTest(vehicle9);

        System.out.println("\nTEST 10: INVALID LOCATION");
        CampusVehicle vehicle10 =
                new CampusVehicle("MU2003", "Walmart", true);
        runTest(vehicle10);


        // Requirement 7: Test different capitalization
        System.out.println("\nTEST 11: CASE INSENSITIVITY");
        CampusVehicle vehicle11 =
                new CampusVehicle("mu1234", "lIbRaRy", true);
        runTest(vehicle11);

        // Requirement 2: Test minimum ID length (4)
        System.out.println("\nTEST 12: ID LENGTH 4");
        CampusVehicle vehicle12 =
                new CampusVehicle("MU12", "Parking Lot", true);
        runTest(vehicle12);

        // Requirement 2: Test maximum ID length (12)
        System.out.println("\nTEST 13: ID LENGTH 12");
        CampusVehicle vehicle13 =
                new CampusVehicle("MU1234567890", "Laurel Hall", true);
        runTest(vehicle13);

        System.out.println("\nALL TESTS COMPLETED");
    }


    // Requirements 8(c), 8(e), 8(h), 8(j), 8(l): Print attributes
    public static void printAttributes(CampusVehicle vehicle) {
        System.out.println("ID: " + vehicle.getId());
        System.out.println("Location: " + vehicle.getLocation());
        System.out.println("Available: " + vehicle.isAvailable());
    }


    // Requirements 8(f), 8(k), 8(l): Test vehicle availability
    public static void testCheckoutReturn(CampusVehicle vehicle) {
        System.out.println("Before checkout: " + vehicle.isAvailable());

        vehicle.checkout();
        System.out.println("After checkout: " + vehicle.isAvailable());

        // Requirement 6: An unavailable vehicle stays unavailable
        vehicle.checkout();
        System.out.println("After second checkout: " + vehicle.isAvailable());

        vehicle.returnVehicle();
        System.out.println("After return: " + vehicle.isAvailable());
    }


    // Requirement 8(l): Print attributes and test vehicle
    public static void runTest(CampusVehicle vehicle) {
        printAttributes(vehicle);
        testCheckoutReturn(vehicle);
    }
}
