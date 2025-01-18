---
ns: VEHICLE
---

## _ATTACH_CONTAINER_TO_HANDLER_FRAME


// 0x6A98C2ECF57FA5D4 0x20AB5783
void _ATTACH_CONTAINER_TO_HANDLER_FRAME(Vehicle handler, Entity container);
Description
The _ATTACH_CONTAINER_TO_HANDLER_FRAME function is a native API method in the VEHICLE namespace that allows developers to attach an entity, such as a container or other object, to a specified vehicle's handler frame. This is particularly useful for creating dynamic interactions between vehicles and their components, such as attaching trailers, cargo, or custom-modifiable parts to a vehicle.

Once attached, the container entity moves and rotates in synchronization with the handler vehicle. This function can be employed in a variety of gameplay scenarios, including but not limited to:

Customizing vehicles with additional components.
Simulating transport mechanics where objects must be firmly fixed to vehicles.
Scripted cutscenes or events that require seamless integration of objects with vehicles.
Parameters
handler (Vehicle):
The primary vehicle to which the container or object will be attached. This parameter expects a valid vehicle entity. Ensure the vehicle has a handler frame to allow for proper attachment.

container (Entity):
The object or container that will be attached to the handler vehicle. The entity must be active, spawned, and positioned within the game world before calling this function.

Usage Notes
Collision Awareness:
When attaching a container, consider the positioning and dimensions to avoid unintended collisions with the vehicle or surrounding objects.

Entity States:
Both the handler (vehicle) and container (entity) must be valid and fully initialized entities. An invalid or missing entity will result in the function failing silently or returning errors in logs.

Dynamic Interaction:
Attached entities inherit the vehicle's movement and rotation. However, depending on your gameplay requirements, additional adjustments may be needed for accurate alignment or behavior.

Detachment:
To detach the container from the vehicle, use a complementary function (if available) or manually reset the container’s position and parent entity.

Debugging:
If attachment appears misaligned, verify the handler frame's coordinates and the container's initial positioning before calling this function.

Example
Below is an example demonstrating how to attach a container to a vehicle using this function:

c
Copy
Edit
// Example: Attach a container to a vehicle
Vehicle truck = GetVehicleByID(123); // Retrieve or spawn the truck
Entity trailer = SpawnEntity("trailer_model"); // Spawn a trailer entity

if (IsEntityValid(truck) && IsEntityValid(trailer)) {
    // Attach the trailer to the truck's handler frame
    _ATTACH_CONTAINER_TO_HANDLER_FRAME(truck, trailer);
} else {
    Print("Error: Invalid vehicle or container entity.");
}
Common Use Cases
Transport Missions:
Attach cargo containers or trailers to vehicles for delivery missions, ensuring they remain fixed during transit.

Custom Vehicles:
Create modular vehicle designs by dynamically adding or replacing parts.

Dynamic Gameplay:
Implement scenarios where objects can be picked up and attached to vehicles as part of interactive missions or events.

Scene Setup:
For cutscenes or cinematic purposes, use this function to integrate props or objects with vehicles for a seamless presentation.

