# two-points-in-geodesy-
Point positioning solved by computation from measurements.


import java.text.DecimalFormat;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        double x1, x2, y1, y2;
        double vinkel;
        double connect_vinkel1,connect_vinkel2,connect_vinkel3 = 0;
        double direction_vinkel1,direction_vinkel2,direction_vinkel3 = 0;
        double deltaX1,deltaY1,deltaX2,deltaY2;
        double distans1,distans2;
        double X3,Y3,X4,Y4=0;

        Scanner scanner = new Scanner(System.in);
        System.out.println("enter koordinate x1:");
        x1 = scanner.nextDouble();
        System.out.println("enter koordinate x2:");
        x2 = scanner.nextDouble();
        System.out.println("enter koordinate y1:");
        y1 = scanner.nextDouble();
        System.out.println("enter koordinate y2:");
        y2 = scanner.nextDouble();
        System.out.println("enter connect vinkel1");
        connect_vinkel1 = scanner.nextDouble();
        System.out.println("enter distans1");
        distans1 = scanner.nextDouble();
        System.out.println("enter connect vinkel2");
        connect_vinkel2 = scanner.nextDouble();
        System.out.println("enter distans2");
        distans2 = scanner.nextDouble();
        scanner.close();
        DecimalFormat df=new DecimalFormat(" .00");

        {
            if (x2 >= x1 && y2 >= y1) {
                vinkel = Math.toDegrees(Math.atan((x2 - x1) / (y2 - y1)));
                System.out.println("vinkel = " + vinkel);
            } else if (x2 >= x1 && y2 <= y1) {
                vinkel = Math.toDegrees(Math.atan(Math.abs((x2 - x1) / (y2 - y1)))) + 90;
                System.out.println("vinkel = " + (vinkel));
            } else if (x2 <= x1 && y2 <= y1) {
                vinkel = Math.toDegrees(Math.atan(Math.abs((x2 - x1) / (y2 - y1)))) + 180;
                System.out.println("vinkel = " + (vinkel));
            } else {
                vinkel = Math.toDegrees(Math.atan(Math.abs((x2 - x1) / (y2 - y1)))) + 270;
                System.out.println("vinkel = " + (vinkel));
            }
        }
        if ((vinkel + connect_vinkel1) > 180) {
            direction_vinkel1 = ((vinkel + connect_vinkel1) - 180);
        } else {
            direction_vinkel1 = ((vinkel + connect_vinkel1) + 180);
        }

        if (direction_vinkel1>360) {
            while (direction_vinkel1>360)
                direction_vinkel1=direction_vinkel1-360;
        }
        System.out.println("direction_vinkel1= " + direction_vinkel1);
        {
            deltaX1 = ((Math.cos(direction_vinkel1*Math.PI/180)) * distans1);
            System.out.println(("deltaX1= " + df.format(deltaX1)));
            deltaY1 = ((Math.sin(direction_vinkel1*Math.PI/180)) * distans1);
            System.out.println(("deltaY1= " + df.format(deltaY1)));
        }
            X3 = (x2 + deltaX1);
            Y3 = (y2 + deltaY1);
            System.out.println("X3= " + df.format(X3));
            System.out.println("Y3= " + df.format(Y3));

            if ((direction_vinkel1 + connect_vinkel2) > 180) {
                direction_vinkel2 = ((direction_vinkel1 + connect_vinkel2) - 180);

            } else {
                direction_vinkel2 = ((direction_vinkel1 + connect_vinkel2) + 180);
            }

            if (direction_vinkel2>360) {
                while (direction_vinkel2>360)
                    direction_vinkel2=direction_vinkel2-360;
            }
        System.out.println("direction_vinkel2= " + direction_vinkel2);
            {
                deltaX2 =((Math.cos(direction_vinkel2*Math.PI/180)) * distans2);
                System.out.println(("deltaX2 =" + df.format(deltaX2)));
                deltaY2 = ((Math.sin(direction_vinkel2 * Math.PI / 180)) * distans2);
                System.out.println(("deltaY2 =" + df.format(deltaY2)));
            }
            {
                X4 = (X3 + deltaX2);
                Y4 = (Y3 + deltaY2);
                System.out.println("X4 = " + df.format(X4));
                System.out.println("Y4 = " + df.format(Y4));
            }
        }
     }
