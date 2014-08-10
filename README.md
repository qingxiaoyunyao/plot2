plot2
=====

## read data into R
data <- read.csv2("household_power_consumption.txt", header = TRUE, as.is = TRUE) 

## add a new variable "time" which denotes the time and date
time <- strptime(paste(data$Date, data$Time), "%d/%m/%Y %H:%M:%S")

data$time <- time

## transform "Date" variable to Date type
data$Date <- as.Date(data$Date, "%d/%m/%Y")

## get the data from 01/02/2007 to 02/02/2007
a <- data[data$Date >= as.Date("01/02/2007", "%d/%m/%Y") & data$Date <= as.Date("02/02/2007","%d/%m/%Y"),]

## draw the picture
with(a, plot(time, Global_active_power, type = "l", ylab = "Global Active Power (kilowatts)", xlab = ""))

## save the picture in plot2.png
dev.copy(png, width = 480, height = 480, file = "plot2.png")

dev.off()

Exploratory Data Analysis/ assignment 1/ plot2
