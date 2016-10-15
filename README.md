# tarea-4
figuras
(package Ilustrar;

import java.awt.Color;
import java.awt.Graphics;

public class Circunferencia {

    private final int A;
    private final int B;
    private final int C;
    private final int D;
    private final Color Pintura;

    public Circunferencia(int w, int x, int y, int z, Color col) {
        this.A = y;
        this.B = x;
        this.C = y;
        this.D = z;

        Pintura = col;
    }

    public void dibujar(Graphics graph) {

        graph.setColor(Pintura);
        graph.drawOval(A, B, C, D);
        graph.fillOval(A, B, C, D);
    }
}
)
-------------------------------------------------------------------
package Ilustrar;

//Realizado por;
//Almaguer Valenciano Cristo Antonio
//Lara Rodriguez Erik Raul

import javax.swing.JFrame;

public class Dibujo {

    public static void main(String args[]) {
        Panel panel = new Panel();
        JFrame aplicacion = new JFrame();

        aplicacion.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        aplicacion.add(panel);
        aplicacion.setSize(300, 300);
        aplicacion.setVisible(true);
    }
}
----------------------------------------------------------------------------
package Ilustrar;

import java.awt.Color;
import java.awt.Graphics;
import java.util.Random;
import javax.swing.JPanel;

public class Panel extends JPanel {

    private final Random Alea = new Random();
    private final Recta[] Recta; // arreglo de lineas
    private final Circunferencia Ovalo[];
    private final Rectangulo Rectam[];
    // constructor, crea un panel con figuras al azar

    public Panel() {
        setBackground(Color.WHITE);
        Ovalo = new Circunferencia[1 + Alea.nextInt(1)];
        Rectam = new Rectangulo[1 + Alea.nextInt(1)];
        Recta = new Recta[1 + Alea.nextInt(1)];
// _______________________ RECTANGULO _____________________________
        for (int cuenta = 0; cuenta < Rectam.length; cuenta++) {

            int x1 = Alea.nextInt(200);
            int y1 = Alea.nextInt(200);
            int x2 = Alea.nextInt(200);
            int y2 = Alea.nextInt(300);

            Color color = new Color(Alea.nextInt(250),
                    Alea.nextInt(250), Alea.nextInt(250));

            Rectam[cuenta] = new Rectangulo(x1, y1, x2, y2, color);
        } // fin de for

// ______________________ LINEAS __________________________________________
// crea lineas
        for (int cuenta = 0; cuenta < Recta.length; cuenta++) {

            int x1 = Alea.nextInt(300);
            int y1 = Alea.nextInt(300);
            int x2 = Alea.nextInt(300);
            int y2 = Alea.nextInt(450);

// genera un color aleatorio
            Color color = new Color(Alea.nextInt(250),
                    Alea.nextInt(250), Alea.nextInt(250));

            Recta[cuenta] = new Recta(x1, y1, x2, y2, color);
        } // fin de for
//_______________________ OVALO _________________________
        for (int cuenta = 0; cuenta < Ovalo.length; cuenta++) {
            int x = Alea.nextInt(400);
            int y = Alea.nextInt(350);
            int w = Alea.nextInt(400);
            int h = Alea.nextInt(500);

// genera un color aleatorio
            Color color = new Color(Alea.nextInt(250),
                    Alea.nextInt(250), Alea.nextInt(250));

// agrega la lÃ­nea a la lista de lÃ­neas a mostrar en pantalla
            Ovalo[cuenta] = new Circunferencia(x, y, w, h, color);
        }
    } // fin del constructor de Panel

// para cada arreglo de figuras, dibuja las figuras individuales
    public void paintComponent(Graphics g) {
        super.paintComponent(g);

// dibuja las lÃ­neas
        for (Recta linea : Recta) {
            linea.dibujar(g);
        }
// dibuja las ovalos
        for (Circunferencia ovalos : Ovalo) {
            ovalos.dibujar(g);
        }
// dibuja las rectangulos
        for (Rectangulo rectangulos : Rectam) {
            rectangulos.dibujar(g);
        }
    }

// fin del mÃ©todo paintComponent
}
------------------------------------------
package Ilustrar;

import java.awt.Color;
import java.awt.Graphics;

public class Recta {

    private final int x1;
    private final int y1;
    private final int x2;
    private final int y2;
    private final Color Pintura;

    public Recta(int q, int w, int e, int r, Color col) {
        this.x1 = q;
        this.y1 = w;
        this.x2 = e;
        this.y2 = r;
        Pintura = col;
    }

    public void dibujar(Graphics graph) {
        graph.setColor(Pintura);
        graph.drawLine(x1, y1, x2, y2);
    }
}
------------------------------------------------------
package Ilustrar;

import java.awt.Color;
import java.awt.Graphics;

public class Rectangulo {

    private final int A;
    private final int B;
    private final int C;
    private final int D;
    private final Color Pintura;

    public Rectangulo(int w, int x, int y, int z, Color col) {
        this.A = y;
        this.B = x;
        this.C = y;
        this.D = z;

        Pintura = col;
    }

    public void dibujar(Graphics graph) {

        graph.setColor(Pintura);
        graph.drawRect(A, B, C, D);
        graph.fillRect(A, B, C, D);
    }
}
------------------------------
