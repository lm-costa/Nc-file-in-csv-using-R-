# Nc-file-in-csv (using R)
Transform and extract data from a .nc file 


# library nescessary 

library(raster)

library(ncdf4)

library(readxl)

library(xlsx)


# clean your Environment

rm(list=ls())

# Select the .nc file

nc.brick <- brick(file.choose())

# creating a first data frame 

nc.df <- as.data.frame(nc.brick[[1]], xy=T)

# excluding Null data

nc.df2 <- na.omit(nc.df)

# Select the variables that you are gonna use 

nc.df3 <- as.data.frame(nc.df2$variable_1,...nc.df2$nc.variable_n)

# if you need to specific geographics coordinates

nc.df4<-subset(nc.df3, superior limit > y & y>inferior limit) #limits to the desired latitude

nc.df5 <- subset(nc.df4, superior limit>x & x> inferior limit) #limits to the desired longitude

# final 

nc.final <- nc.df5 #if you don't limit your data use the nc.df3

# data test

max(nc.final$variable_desired, na.rm=T)

min(nc.final$variable_desired, na.rm=T)

mean(nc.final$variable_desired, na.rm=T)

sd(nc.final$variable_desired, na.rm=T)

hist(nc.final$variable_desired, na.rm=T)

# transform in csv

write.csv(nc.final, file= "C:/place/name.csv)
