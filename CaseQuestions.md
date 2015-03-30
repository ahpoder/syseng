# General #

  1. In the requirements there is assumed access to many technical documents (MIL-1553B, body frame format, inertial format, F16 EW compatibility requirements, etc.). As detailed info of these are not necessary for the system requirements or overall design from an educational perspective, we would like to simply pretend they exist and that we are knowledgeable in them. Where the protocols directly relate to requirements we ask questions below as needed.
    * This is perfectly OK, and we may even invent standards where details domain knowledge would otherwise be required, e.g. the POD size/material requirements.
  1. No details about GUI design is present (light intensity, font, colour, ...), and we would like to postpone this or simply say that it is an existing and approved document. Is this acceptable?
    * No GUI should be made what so ever. Simply make sure the design has access to the information we wish to display and then assume that it can be displayed in a satisfactory manor - same is true for Dispenser programming. Simply assume that a PC application that can generate a Dispenser program on a loading device of our choice exist.
  1. The dispensing programs are very complicated involving many factors such as thread type, direction velocity, leathality, etc. As we believe it is not feasible to program these on the plane, we would like to assume that a PC application exist that can create these programs, and that this application is not part of the project. Is this acceptable?
    * See above.

# High priority #
  1. What is the efficiency of the PCU?
    * We may assume 100%
  1. What is the weight of a magazine and should it be included in the total weight of the POD? (max 270kg)
    * Magazines should not be counted towards the weight and it is therefore not relevant.
  1. Can we save 2 DSSs by fixing which direction has 4 magazines and which has 2, or must all Dispensers have 2 DSSs, where we for power reasons only turn one for two of the directions?
    * Yes, we may arrange the magazines as we wish, as long as there is at least 1 magazine per dispenser.
  1. Not compromise current weapons systems (UR-3) - is that only with respect to EMC and the communication bus, or is it also the fact that the POD takes up space which could be used for weapons, changes the planes aerodynamic shape and weight and therefore its maneuverability? Is the ECU hooked up to the planes databus (MIL-1553), or do we have a dedicated MIL-1553 controller in the cockpit-unit (UR-40), so it can be master? The MIL-1553 data-bus has a 1MBit bandwidth with a single master. How often and how much can we communicate without disturbing the EW systems?
    * We may refer to standards for design and implementation as well as perform EMC and noise tests. There is allowed to be 2 databusses, so we do not have to worry about that
  1. Details about the status and built in test results are missing (UR-6) - what exactly are we sending? (May require dedicated discretes to the POD to be able to comply)
    * See GUI description above.
  1. Erasing sensitive data (UR-9) - what are the performance requirements? How fast? May we assume that power is supplied, or do we have to support an off-line solution (explosives)? Are we allowed to rely on encryption and just erase the key? Where is the sensitive data stored, only in the MWS or in both the MWS and cockpit unit?
    * We can make up the specifications.
  1. The level of system status (UR-10) is not specified. Is it the remaining payload on each magazine? In each dispenser? Just that they are operational/empty? Misfire count? Sensor status? DSS status?
    * We should specify which LRU's we want to register status for (DSS, Magazine, POD, ...), but not how.
  1. The dimensions of the cockpit unit is missing, so we do not know the allowed size of the display for system status (UR-10).
    * We should simply assume that there is room and that it is within view and reach of the pilot.
  1. How do the pilot select the program to fire when using manual dispense (UR-13)? Is it to be selected on the cockpit unit? How many programs can there by all together to choose from?
    * We may assume a fixed number of programs and that the pilot have a dedicated button or a menu - it is up to us.
  1. Is it actually a requirement that two dispenser can fire at the "same time" (UR-20), i.e. within 20ms, or is a program allowed to fire one dispenser at a time? (1 dispenser fire and then 20ms later the next dispenser fire). Can two dispensers firing witin 40ms be said to be "at the same time"? Is there a maximum engagement time (or shots fired) so we can store the required effect in a capacitor?
    * We are allowed to say that two dispensers firing in 40ms is "at the same time" and we do therefore not need extra power. We may also use capacitors or other power storing if we wish.
  1. Optimal coverage (UR-22) is untestable - what level of coverage is acceptable?
    * We should write a requirement as to what level of coverage they can have: e.g. 120 degree back, 180 degrees left, 120 degrees forward and NA degrees right.
  1. What is the insulating qualities of the POD and what is the heat-generation of the MWS? How do we know if extra cooling is needed?
    * We may simply refer to a non-existing standard or we can make up a heat signature - it is up to us.
  1. What is an acceptable latency for navigation data coming from the mission computer to the MWS? If the MWS do not have direct access to the MIL1553 bus of the aircraft mission computer this will introduce an extra latency in copying in the cockpit unit, but if there are not two buss' then the aircraft mission computer must be configured to service the cockpit unit to/from MWS, as it is required that the aircraft mission computer is master to ensure UR-3.
    * It is allowed to have two data busses, with the latency that creates - we should simply change the requirement to indicate the maximum latency they can get.

# Lower priority #
  1. What are the dimensions of the magazine?
    * Irrelevant
  1. How many payloads do they hold?´
    * 30 - 60, but it is irrelevant
  1. The hardware implemented safety interlock (UR-8), is that a physical pin on the POD or/and a discrete PLANE ON GROUND?
    * No requirement for a PLANE ON GROUND discrete. Hardware implemented means not controllable from software.
  1. Control power - dows that mean we should be able to intelligently power down parts of the MWS, or should we just be able to turn it on and off?
    * We should just be able to turn it on and off