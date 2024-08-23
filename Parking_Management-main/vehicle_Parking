class Vehicle:
    def __init__(self, num, row, col, vtype):
        self.num = num
        self.row = row
        self.col = col
        self.type = vtype


parkinfo = [[0] * 10 for _ in range(4)]
vehcount = 0
carcount = 0
scootercount = 0


def display():
    print("\nCars =>")
    for row in parkinfo[:2]:
        print("\t".join(map(str, row)))
    print("\nScooters =>")
    for row in parkinfo[2:]:
        print("\t".join(map(str, row)))


def add(t, num, row, col):
    global vehcount, carcount, scootercount
    v = Vehicle(num, row, col, t)

    if t == 1:
        carcount += 1
    else:
        scootercount += 1

    vehcount += 1
    parkinfo[row][col] = num

    return v


def del_vehicle(v):
    c = v.col
    for c in range(v.col, 9):
        parkinfo[v.row][c] = parkinfo[v.row][c + 1]

    parkinfo[v.row][c] = 0

    if v.type == 1:
        global carcount
        carcount -= 1
    else:
        global scootercount
        scootercount -= 1

    global vehcount
    vehcount -= 1


def get_free_row_col(vtype):
    fromrow, torow = 0, 2

    if vtype == 2:
        fromrow += 2
        torow += 2

    for r in range(fromrow, torow):
        for c in range(10):
            if parkinfo[r][c] == 0:
                return r, c

    return -1, -1


def get_rc_by_info(vtype, num):
    fromrow, torow = 0, 2

    if vtype == 2:
        fromrow += 2
        torow += 2

    for r in range(fromrow, torow):
        for c in range(10):
            if parkinfo[r][c] == num:
                return r, c

    return -1, -1


def login():
    a = 0
    while a <= 2:
        uname = input("\nEnter username: ")
        pword = input("Enter password: ")
        if uname == "admin" and pword == "admin":
            print("Login successful!")
            return
        else:
            print("Login unsuccessful!")
            a += 1
    print("Sorry, you have entered the wrong username and password for four times!")


def main():
    login()

    while True:
        print("\n\tVEHICLE PARKING")
        print("\n1. Arrival of Vehicle")
        print("2. Total Number of Vehicles Parked")
        print("3. Total Number of Cars Parked")
        print("4. Total Number of Scooters Parked")
        print("5. Display Vehicles Parked (Order)")
        print("6. Departure of Vehicle")
        print("7. Exit")

        choice = int(input("\nEnter your choice: "))

        if choice == 1:
            vtype = 0
            while vtype not in [1, 2]:
                vtype = int(input("Enter vehicle type (1 for Car / 2 for Scooter): "))
                if vtype not in [1, 2]:
                    print("Invalid vehicle type.")

            number = int(input("Enter vehicle number: "))

            if vtype in [1, 2]:
                row, col = get_free_row_col(vtype)
                if row != -1 and col != -1:
                    vehicle = add(vtype, number, row, col)
                else:
                    if vtype == 1:
                        print("No parking slot free to park a car.")
                    else:
                        print("No parking slot free to park a scooter.")
            else:
                print("Invalid type.")

        elif choice == 2:
            print("Total vehicles parked:", vehcount)

        elif choice == 3:
            print("Total cars parked:", carcount)

        elif choice == 4:
            print("Total scooters parked:", scootercount)

        elif choice == 5:
            print("\nDisplay")
            display()

        elif choice == 6:
            vtype = 0
            while vtype not in [1, 2]:
                vtype = int(input("Enter vehicle type (1 for Car / 2 for Scooter): "))
                if vtype not in [1, 2]:
                    print("Invalid vehicle type.")

            number = int(input("Enter vehicle number: "))

            if vtype in [1, 2]:
                row, col = get_rc_by_info(vtype, number)
                if row != -1 and col != -1:
                    del_vehicle(Vehicle(number, row, col, vtype))
                else:
                    if vtype == 1:
                        print("Invalid car number or a car with such number has not been parked here.")
                    else:
                        print("Invalid scooter number or a scooter with such number has not been parked here.")
            else:
                print("Invalid type.")

        elif choice == 7:
            break

        input("\nPress Enter to continue...")


if __name__ == "__main__":
    main()
