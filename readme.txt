clc
clear all
v=input("Enter the dimension :")                           %Dimension of shape
for i=1:v
    O(i)=input("Enter the origin coordinates :")           %Coordinates of origin
end
for i=1:v
    C(i)=input("Enter the centre coordinates :")           %Coordinates of centre
    Cvector(i)=C(i)-O(i);                                  %Centre w.r.t Origin
end
r=input("Enter the radius")                                %Radius of circle
A1=pi*r^2;
for i=1:v
    th = 0:pi/50:2*pi;
    xunit = r * cos(th) + Cvector(i);                      %dimensions of circle
    yunit = r * sin(th) + Cvector(i);
    centroid(i)=Cvector(i);
    hold on
end

n = input('Enter your choice for slot : 1.Circle   2.Triangle   3.Rectangle');
switch n
    case 1 
        for i=1:v
            Slot(i)=input("Enter the centre coordinates :")           %Coordinates of centre(slot)
            Cslotvector(i)=Slot(i)-O(i);                              %Centre w.r.t Origin(slot)
        end
        rslot=input("Enter the radius")                                %Radius of circle(slot)
        A2=pi*rslot^2;
        for i=1:v
            th = 0:pi/50:2*pi;
            xslotunit = rslot * cos(th) + Cslotvector(i);             %dimensions of slot
            yslotunit = rslot * sin(th) + Cslotvector(i);
            plot(xunit,yunit,xslotunit,yslotunit);                    %plotting the circle with slot(circle)
            slotcentroid(i)=Cslotvector(i)
        end
        k=input("Enter your choice for Moment of Inertia : 1.About centroidal axes    2.About x- and y- axes")
        switch k
            case 1
                n1=pi*r^4/4;
                n2=pi*rslot^4/4;
                display("The moment of inertia about the centroidal axis is")
                display(n1-n2)
            case 2
                %display("The moment of inertia about x axis is")
                n1=pi*r^4/4;
                n2=pi*rslot^4/4;
                for i=1:v
                    m1=A1*Cvector(i)^2;
                    m2=A1*Cslotvector(i)^2;
                    m3=A1*Cvector(i)^2;
                    m4=A2*Cslotvector(i)^2;
                end
                M3=n1+m3;
                M4=n2+m4;
                display("The moment of inertia about x axes is")
                display(M3-M4)
                M1=n1+m1;
                M2=n2+m2;
                display("The moment of inertia about the y axis is")
                display(M1-M2)
        end
    case 3
        for i=1:v
            r(i)=input("Enter any one of the rectangle cordinates");
            r2(i)=r(i)-O(i)
        end
        %l=input("Enter the length of the rectagle");
        %b=input("Enter the breadth of the rectangle");
        %for i=1:v
         %   rectangle('Position',[r2(i),r2(i),l,b])
          %  axis([O(i),20,O(i),20])
        %end
        
        %k=input("Enter your choice for Moment of Inertia : 1.About centroidal axes    2.About x- and y- axes")
        %switch k
        
       
                    
                
                
                    
            
            
            
                                       
                
    end


