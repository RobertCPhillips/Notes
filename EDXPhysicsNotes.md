# EDX Physics Notes

This is my attempt to summarize points as I work through these classes.

## Chap 16 - 2D Rotational Kinematics

#### Rigid Body / Fixed Axis Rotation
  - Given a rigid body and a fixed axis of rotation, each individual element **i** of the body is moving in a circle with radius **r_i**
  - All elements of the body have the same angular velocity and same angular acceleration
  - Recall the definition of angular velocity **omega_z = theta'** and angular acceleration **alpha_z = theta''**
  - Also recall definition of tangential velocity **v_i = r_i * omega_z** and tangential acceleration **a_i = r_i * alpha_z**
  - Futhermore, recall in inward acceleration with a radial component **a = -r_i * omega_z^2 = -v_i^2/r_i**

#### Rotational Kinetic Energy and Moment of Inertia
  - Recall translational kinetic energy **K = 1/2 * m * v^2**
  - Given a fixed axis passing through center of mass, each mass element **i** is moving in a circle about center of mass with angular velocity **omega** and radius **r_i**.  Thus the (tangential) velocity of each mass element is **r_i * omega**, this gives **K = 1/2 * r_i^2 * omega^2**
  - Summing all of the mass elements yields **1/2 * (integral dm * r^2) * omega^2**, the integral portion is refered to as the **moment of intertia** 
  - Computing the integral often involves defining model for dm and r in terms of a common integration variable.
    - determine model for size (i.e. length, area, volume) of element 
    - determine mass of element which is total mass / total size (e.g. length or area or volume) * size of element
    - the above is for uniform objects

  - Parallel Axis Theorem - given the axis for the center of mass and another parallel axis S, then **I_s = I_cm + m * d_s^2**, 

  - Recall that given a closed system and only conservative internal forces, the change in mechanical energy (kinetic, potential) of a system is 0 (e.g. **deltaU_f + deltaK_f = deltaU_i + deltaK_i**). Kinetic energy for rotation is given above.
  - as an example, we can use this to incorporate pulley mass in to problems.

## Chapter 17 - 2d Rotational Dynamics (Torque, Angular Acceleration, and Moment of Inertia)
  - Torque and angular acceleration are related by an objects moment of inertia
  - The torque produced by a **F** at a point **P** with respect to a point **S** is the cross product of the vector r_sp and F_p.

  - Given a body rotating about an axis and a point **S** on that axis, the torque on an individual mass element is the cross product of vector from **S** to the mass element and the force acting on that mass element (with perpendicular distance **r** from the axis) 
  - Furthermore, applying F=ma and the angular acceleration giving a tangential accerlation of **r * alpha**, the torque of the mass element is **m * r^2  * alpha**. Since **alpha** is the same for all elements, the sum of torque for all elements is **alpha * sum(m_i * r_i^2)** which is I * alpha.

## Chapter 19 - Angular Momentum
  - For a point like particle, the the angular momentum **L** about a point **S** is defined as the cross product of r_s with p (the particles linear momentum). I.e. **L_s = r_s x p**
  - This yields torque as the change in angular momentum (just as impulse is to change in linear momentum)
    - L = I_s * omega_s, so L' = I_s * omega' = I_s * alpha = torque
  - Given a rigid body of n elements with rotation about a fixed axis and some point **S** on that axis, the the angular momentum is the sum of angular momenta of each element.

  - Given a system of particles, the angular momentum of particle **i** is r_i x p_i.  The angular momentum of the system is the sum of individual angular momenta.
  - Given a system of particles with zero momentum, the angular momentum about any point is 0. This is shown by deriving the relationship of the angular momentum about 2 differnt points for the same system. (e.g. A and B, L_a = L_b + r_ab x p)

  - Given an object and a fixed axis that is not symmetric, the angular momentum about a point on the axis depends on the location of the point. Additionally, the angular momentum is parallel only when calculated at the point of intersection between the axis of rotation and the object

  - When a symmetric object rotates about the axis of symmetry, the angular momentum about a given point on the axis is independent of the location of point

#### Conservation of Angular Momentum about a Point
  - Recall that energy and momentum are conserved in closed systems
  - This indicates that if the external force is 0 in any direction, the change in momentum in that component is 0.
  - Give a point about which the torque is 0, then the change in angular momentum about that point is 0 (i.e. constant)

#### Angular Impulse
  - Angular impulse is defined as a total torque applied over an interval time, given by the time integral of torque
  - This is also equal to a change in angular momentum, just as linear impulse is the change in momentum.
  - if the torque (impulse) is 0, then angular momentum is constant

## Chap 20 Translation and Rotational Motion for Fixed Axis Rotation
  - 





