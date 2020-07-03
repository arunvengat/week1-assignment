# week1-assignment
coursera assignment
# plot 1
data <- read.table("household_power_consumption.txt",sep = ";",header = TRUE,na.strings = "?")
data$Date <- as.Date(data$Date, format = "%d/%m/%Y")
data$Global_ative_power <- as.numeric(data$Global_active_power)
s <- (data$Date == "2007-02-01" | data$Date == "2007-02-02")
i_data <- data[s,]
png("plot1.png")
hist(i_data$Global_active_power,col = "red",xlab = "Global Active Power (kilowatts)",main = "Global Active Power")
dev.off()
# plot 2
d <- read.table("household_power_consumption.txt",sep = ";",header = TRUE,na.strings = "?")
d$Global_ative_power <- as.numeric(d$Global_active_power)
d$dateTime <- as.POSIXct(paste(d$Date,d$Time),format = "%d/%m/%Y %H:%M:%S")
d <- d[(d$dateTime>="2007-02-01") & (d$dateTime < "2007-02-03"),]
png("plot2.png")
plot(x=d$dateTime,y=d$Global_active_power,type="l",xlab="",ylab="Global Active Power(kilowatts)",main="")
dev.off() 
# plot 3
d <- read.table("household_power_consumption.txt",sep = ";",header = TRUE,na.strings = "?")
d$Global_ative_power <- as.numeric(data$Global_active_power)
d$dateTime <- as.POSIXct(paste(d$Date,d$Time),format = "%d/%m/%Y %H:%M:%S")
d <- d[(d$dateTime>="2007-02-01") & (d$dateTime < "2007-02-03"),]
png("plot3.png")
plot(x=d$dateTime,y=d$Global_active_power)
plot(x=d$dateTime, y = d$Sub_metering_1,type = "l",xlab = "",ylab = "Energy sub metering",main = "",col = "black")
points(x=d$dateTime, y = d$Sub_metering_2,type = "l",xlab = "",ylab = "Energy sub metering",main = "",col = "red")
points(x=d$dateTime, y = d$Sub_metering_3,type = "l",xlab = "",ylab = "Energy sub metering",main = "",col = "blue")
dev.off() 
# plot 4
data <- read.table("household_power_consumption.txt",sep = ";",header = TRUE,na.strings = "?")
data$Global_active_power <- as.numeric(data$Global_active_power)
data$dateTime <- as.POSIXct(paste(data$Date,data$Time),format = "%d/%m/%Y %H:%M:%S")
data <- data[(data$dateTime>="2007-02-01") & (data$dateTime < "2007-02-03"),]
png("plot4.png")
par(mfrow=c(2,2))

plot(x=data$dateTime,y=data$Global_active_power,type = "l",xlab="",ylab="Global Active Power(kilowatts)",main="")

plot(x=data$dateTime,y = data$Voltage, type = "l",xlab = "datetime",ylab = "Voltage",main="")

plot(x=data$dateTime, y = data$Sub_metering_1,type = "l",xlab = "",ylab = "Energy sub metering",main = "",col = "black")
points(x=data$dateTime, y = data$Sub_metering_2,type = "l",xlab = "",ylab = "Energy sub metering",main = "",col = "red")
points(x=data$dateTime, y = data$Sub_metering_3,type = "l",xlab = "",ylab = "Energy sub metering",main = "",col = "blue")

plot(x=data$dateTime,y=data$Global_active_power,type = "l",xlab="datetime",ylab="Global_reactive_power",main="")

dev.off() 
