# Spread-reate-of-a-virus-using-NetLog0
globals [%infected]

to setup
  clear-all
  reset-ticks
  create-turtles population_in_simulation
  [
    setxy random-xcor random-ycor
    set shape "person"
    set color green
  ]

  ask turtle 1 [ set color red ]
  set %infected (count turtles with [color = red] / count turtles) * 100
end

to go
  tick
  ask turtles
    [rt random 100 lt random 100 fd 1]
  ask turtles with [color = red]
    [ask other turtles-here [if random 100 < %infectiousness
      [set color red]]
    ]

set %infected (count turtles with [color = red] / count turtles) * 100
if %infected = 100 [stop]
end
