Code for exercise of course R Programming / Código para el ejercicio de R Programming

CÓDIGO PARA CREAR LA FUNCIÓN CORR DEL CURSO R PROGRAMMING

A continuación se comparte el código creado para la función CORR, Si alguien encuentra alguna mejora es totalmente bienvenida.

In the next lines you can see the code written for create the function CORR. If someone finds one improve, it's totally welcome

########### CORR #################
##### AUTHOR: ESAÚ CONTRERAS
##### DATE : 2019-09-01
##### DESCRIPTION: FUNCTION FOR READ FILES AND CALCULATE
##### THE CORRELATION BETWEEN SULFATE AND NITRATE WITH 
##### OBSERVATIONS GREATER THAN THRESHOLD
##########################################

 #GET DIRECTORY
getwd()

 #SAVE THE PATH IN AN OBJECT
path<-"C:/Users/PC/Documents/specdata/"
path

 #SAVE THE FILES IN DIRECTORY IN AN OBJECT
files<-list.files("C:/Users/PC/Documents/specdata/")
files

 #UPLOAD COMPLETE FUNCTION
source("complete.r")

 #FUNCTION DEFINITION
corr<-function(path, threshold = 0) {

data1<-complete(path)

data2<-subset(data1[data1[2]>threshold,])
x<-c(data2$id)
x[211]
   dat3 <- vector(mode = "numeric", length = 0)

	for (i in x){
		data4<-read.csv(paste0(path,files[i]),header=TRUE)
		data5<-subset(data4[!is.na(data4[2])&!is.na(data4[3]),])
		datacor<-cor(data5[2],data5[3])
		dat3<-c(dat3,datacor)
}

dat3
}

 #TEST FUNCTION
cr<-corr(path,400)
head(cr)
summary(cr)
cr

