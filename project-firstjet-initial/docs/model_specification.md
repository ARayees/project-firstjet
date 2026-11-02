# Model Specification — Version 0.1

## Scope

Version 0.1 is an annualized single-aircraft scenario model. It is not a valuation of First Jet Airways and does not claim to forecast the company's actual results.

## Core terminology

- **Seats:** Passenger seats available on each departure.
- **Load factor:** Passengers divided by seats available.
- **Block time:** Time from aircraft departure from the gate to arrival at the destination gate.
- **Variable cost:** A cost that changes with flying activity or passenger volume.
- **Fixed cost:** A cost that does not change directly with the number of passengers.
- **Contribution:** Revenue remaining after the modeled operating costs.
- **Break-even load factor:** The load factor at which modeled revenue equals modeled costs.

## Inputs

| Input | Unit | Source classification |
|---|---:|---|
| Seats per departure | seats | Comparable aircraft / scenario |
| Flights per day | departures/day | Scenario |
| Operating days | days/year | Scenario |
| Block time | hours/departure | Comparable aircraft / route |
| Load factor | % | BTS/comparable benchmark/scenario |
| Average base fare | USD/passenger | BTS/comparable benchmark/scenario |
| Ancillary revenue | USD/passenger | Comparable airline benchmark/scenario |
| Members | members | First Jet disclosure or scenario |
| Annual membership fee | USD/member/year | First Jet disclosure or scenario |
| Member passenger share | % | Scenario |
| Member fare discount | % | Scenario |
| Fuel burn | gallons/block hour | Aircraft benchmark |
| Jet fuel price | USD/gallon | EIA/scenario |
| Crew cost | USD/block hour | Comparable benchmark/scenario |
| Maintenance cost | USD/block hour | Comparable benchmark/scenario |
| Airport/handling cost | USD/departure | Comparable benchmark/scenario |
| Other variable cost | USD/passenger | Comparable benchmark/scenario |
| Annual aircraft fixed cost | USD/year | Comparable benchmark/scenario |
| Annual allocated overhead | USD/year | Scenario |

## Formula definitions

```text
annual_departures = flights_per_day * operating_days
annual_seats = seats * annual_departures
annual_passengers = annual_seats * load_factor
annual_block_hours = annual_departures * block_time

member_passengers = annual_passengers * member_passenger_share
nonmember_passengers = annual_passengers - member_passengers
member_fare = average_fare * (1 - member_discount)

ticket_revenue = (member_passengers * member_fare) + (nonmember_passengers * average_fare)
ancillary_revenue = annual_passengers * ancillary_revenue_per_passenger
membership_revenue = members * annual_membership_fee
total_revenue = ticket_revenue + ancillary_revenue + membership_revenue

fuel_cost = annual_block_hours * fuel_burn * jet_fuel_price
crew_cost = annual_block_hours * crew_cost_per_block_hour
maintenance_cost = annual_block_hours * maintenance_cost_per_block_hour
airport_cost = annual_departures * airport_cost_per_departure
other_variable_cost = annual_passengers * other_variable_cost_per_passenger

total_cost = fuel_cost + crew_cost + maintenance_cost + airport_cost \
             + other_variable_cost + annual_aircraft_fixed_cost \
             + annual_allocated_overhead

operating_contribution = total_revenue - total_cost
operating_margin = operating_contribution / total_revenue
```

## Modeling cautions

Membership revenue must not be counted twice. In the initial model, membership revenue is shown as a separate revenue stream while member fares are reduced by the member discount. Later versions will distinguish route-level and network-level membership allocation.

All unknown inputs must remain visible and labeled as assumptions. The model should produce ranges and sensitivities, not false precision.
