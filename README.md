def identify_mach_number(velocity, speed_of_sound=343):
    mach = velocity / speed_of_sound

    if mach < 0.3:
        regime = "Incompressible flow"
    elif mach < 1.0:
        regime = "Subsonic"
    elif mach == 1.0:
        regime = "Sonic"
    elif mach < 1.2:
        regime = "Transonic"
    elif mach < 5.0:
        regime = "Supersonic"
    else:
        regime = "Hypersonic"

    return mach, regime


print("Mach Number Identifier")
try:
    velocity = float(input("Enter the object's velocity (m/s): "))
    speed_of_sound = input("Enter the speed of sound (m/s) [press Enter to use 343 m/s]: ")
    speed_of_sound = float(speed_of_sound) if speed_of_sound.strip() else 343

    mach, regime = identify_mach_number(velocity, speed_of_sound)

    print(f"\nMach Number: {mach:.2f}")
    print(f"Flow Regime: {regime}")
except ValueError:
    print("Invalid input. Please enter numeric values.")
