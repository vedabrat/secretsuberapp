# README
This is V1 of an app similar to Uber.

V1 Overview/Storyline: 
Customer’s perspective:
	First stage: the customer wants to get a ride from one place to another and needs to trade 	information with possible drivers in real time. (expectation to minimize conversation waiting 	time) By completing the profile form, the current needs form, and being able to view the current 	live driver’s forms, the conversation can be booked and prepared for in minutes. 
	Second stage: The customer knows the details of the trip and driver, when the ride will arrive, 	what items they need to have ready for the experience. (optional change form is reffered to)
	Third stage: (the experience ensues)/(report a problem/change)
	Fourth Stage: The completion form is issued.
Driver’s perspective:
	First Stage: The driver is looking en route/stalling/parked, awaiting the filling of available space 	within their vehicle. Data is broadcasted. (current amneties form is shown)
	Second stage: The driver is alerted of the imminent call of a customer and a VERY brief trip 	overview and must accept or deny the customer. (accept ride form/display)
	Third stage: Accepted – Driver is presented with route and overview. 
	Fourth stage: (the experience ensues)/(report a problem/change)
	Fifth stage:  The completion form is issued
	
Hurdles
	Customer(C) wants to know:
1How much is a taxi from here(location) to here(location)?
2How long will it take to get here?
3How long is the ride duration?
4Who is the taxi driver?
5Is that driver’s path the same one in my direction?
6Does the driver offer any amneties?
7How good is the driver’s rating?
8Has the driver passed any tests?
9How large is the car?
10(optional)Incentivise me to: rate this car, record all audio in the car, pay in bitcoin, clean this car, cater for others in this car, bring in items into this car, take out items of this car, have a longer trip and get gas with this driver, social profile of the driver, special instructions, comments, medical devices onboard? Profile color type(to explain road priority), needs of the driver, Shared musical likes, ai response wizard for validations(can use trees to figure it out), no interaction

	Driver(D) wants to know:
1What what is the traveller’s trip itinerary?
2What does the customer look like?
3How much space does the customer need? 
4What things does the customer want? 
5What thing does the customer need
6Social profile of the customer
7Would the customer like to control audio or visual effects in the car? 
8What port is needed for handing over video, audio and other sensory applications in the car?
9Is there a special situation for this client
10(optionally)If the client wants to drive my car, what is their driving history? How much tip is expected?, what has the customer studied, what is the customer’s experience rating?

The following 9 forms will help processing speed.

C PROFILE
Social Profile links: automatic/profile
Special Situation? (longterm)?(automatic/profile):(current situation/emergency)
Driving history: automatic/profile
Payment Type: default automatic profile or quickchange
(optional)
Customer rating:
Driving History
Driving experience Rating
Driving resume:

C CURRENT NEEDS
Location 0: current location automatic
Location 1: 
Space needed in vehicle?
Space needed in cargo?
Special Situation? (longterm)?(automatic/profile):(current situation/emergency)
Medical need?
(optional)
Food/beverage needs?
Other needs?
Control Needs: windows/power/port/driver
Services willing to offer? (free)(paid)
Payment Type: default automatic profile or quickchange
Comments

C CHANGE/PROBLEM FORM
Is there an issue/change?
Discuss this with the driver and have them make the changes. 
They should appear shortly after the driver has made the change. 

C COMPLETION FORM
(autoaccept). 
Tip your diver?
Comments about the ride.
Complete this ride (yes/no)

D PROFILE

Driver’s Rating:
Driver’s Comments
D CURRENT NEEDS/AMNETIES

Current location: automatically
End Destination Time:
End Destination Location:

D ACCEPT RIDE
Accept/Deny:

D CHANGE/PROBLEM FORM
Safely pull over/be stopped before you make any changes/reports. 
What needs to be changed? (show options, allow for edits, and then set again)

D COMPLETION FORM

Rate your passenger to drop them off.  
Hurdle Answers
	For synergies, fill out the previous forms. Automatically fill in information that the phone can register. Travel time will be listed in minutes
The current setup is as follows and is due to evoltion: 
	A trip itinerary exists. An api (https://github.com/geokit/geokit-rails) for route planning is used to deliver times, traffic and other updates. 
	All calculations for distances traveled is done for all Long Lat points immediately at the moment the customer requests a booking, and confirms a booking. Live route updates happen at optimum server load intervals. 
If C’s Trip legs/vectors cross over a driver’s Destination Trip, calculate probabilities that they should move together.

	Customer(C) wants to know:
1How much is a taxi from here(location) to here(location)?
Simple Answer: The trip itinerary must be built first. Once the stops are plotted, the total time of the trip according to traffic, and road issues is issued. Expected time is shown. From the expected time of the trip, we divide that by 60 and multiply it by driver’s wage * rating. 
Technical Answer: 
Taxi Cost(TC)=(Average Driver’s Wage(ADW)*(Expected Travel Time in minutes(ETT))/60

(Expected Travel Time in minutes(ETT)) = (Current Location(T0) to Second Location(T1) + (if there is a second location, add a buffer time and time from second location to third location)
2How long will it take to get here?
	
Simple answer: Do the simple calculation from above, and apply it to the drivers location and my location. 	
Technical answer:
Arrival Time(AT) = Driver Location(DLspot) to T0 
3How long is the ride duration? ETT
4Who is the taxi driver? 
Simple Answer: Driver profile
Technical Answer: Show the driver profile page with all displayable information.
5Is that driver’s path the same one in my direction?
Simple answer: See if C’s path and D’s path intersect.
Techincal answer: Use probabilities on trip total time value, weighted trip distance, trip immdiacy, movement probability to figure out if their vectors are aligned right. The best idea to acertain success here is to let the Customer’s vector be super immediate and the driver can use C’s T0 as a portal to get to the far off Destination that is close to C’s T1, T2, or T3
6Does the driver offer any amneties?
Simple answer: Check the driver’s current Needs/Amnities form
technical answer: Let the customer view elements from the Driver’s profile
7How good is the driver’s rating?
Simple answer: Check the driver’s Profile
technical answer: Let the customer view elements from the Driver’s profile
8Has the driver passed any tests?
Simple answer: This should be part of an expansion model for the platform.
Technical answer: view the driver’s profile stats.
9How large is the car?
Simple answer: Check the driver’s Profile
Technical answer: Let the customer view elements from the Driver’s profile. One of the elements will be the car that is registered under his name, with inputs from the array of cars and their sizes. A manual option must be selected, but if the car is within the database, let a choice be automatically entered.
10(optional)Incentivise me to: rate this car, record all audio in the car, pay in bitcoin, clean this car, cater for others in this car, bring in items into this car, take out items of this car, have a longer trip and get gas with this driver, social profile of the driver, special instructions, comments, medical devices onboard? Profile color type(to explain road priority), needs of the driver, Shared musical likes, ai response wizard for validations(can use trees to figure it out), no interaction

	Driver(D) wants to know:
1What what is the traveller’s trip itinerary?
Simple Answer: From T0 to T1
Technical Answer:From T0 to T1 .. or further
2What does the customer look like?
Simple Answer: Let driver view customer profile and profile metrics
Technical Answer: see above.
3How much space does the customer need? 
Simple Answer: See the customer immediate needs form
Technical Answer: see above
4What things does the customer want? 
Simple Answer: see the customer immediate needs form
Technical Answer: see above
5What thing does the customer need
Simple Answer: see the customer immediate needs form
Technical Answer: see above
6Social profile of the customer
Simple Answer: Let driver view customer profile and profile metrics
Technical Answer: see above.
7Would the customer like to control audio or visual effects in the car? 
Simple Answer: see the customer immediate needs form
Technical Answer: see above
8What port is needed for handing over video, audio and other sensory applications in the car?
Simple Answer: see the customer immediate needs form
Technical Answer: see above
9Is there a special situation for this client
Simple Answer: see the customer immediate needs form or customer profile data
Technical Answer: see above
10(optionally)If the client wants to drive my car, what is their driving history? How much tip is expected?, what has the customer studied, what is the customer’s experience rating?
Simple Answer: let the driver fully review the customer driving history in the customer profile
Technical Answer: see above.

*when the word automatically is used, assume integration of an apporpriate gem which returns data in a format you can use javascript to manipulate to a variable within a script.

Technologies needed to be installed: 
Technology			Reason			Concerns		Incremental Costs?
RAILS				Gem Load		Instant Relay speed	React migration
Firebase			User/info database	Users scaling.		As server load increases


Geocoding (unknown)	Waze Deeplinks?
				https://www.waze.com/livemap
				https://developers.google.com/waze/deeplinks/
User module			Devise			Allow authenticated user use only. UX reasons
Figaro				Anonymize data	
Stripe				Payments possible	

Additional Modules required

Administrator interface (at-a-glance view that consists of the following):
	- view metrics of how many users ever, and how many current users
	- user stock chart
	- firebase online
	- # of traffic jams
	- driver ratings
	- customer ratings
	
	- coupon and discount models

	


