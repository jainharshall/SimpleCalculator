import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class SimpleCalculator extends JFrame implements ActionListener {
    JTextField input1, input2, result;
    JButton addBtn, subBtn, mulBtn, divBtn;

    public SimpleCalculator() {
        setTitle("Simple Calculator");
        setSize(400, 250);
        setLayout(new GridLayout(5, 2, 10, 10));
        setDefaultCloseOperation(EXIT_ON_CLOSE);

        add(new JLabel("Enter First Number:"));
        input1 = new JTextField();
        add(input1);

        add(new JLabel("Enter Second Number:"));
        input2 = new JTextField();
        add(input2);

        add(new JLabel("Result:"));
        result = new JTextField();
        result.setEditable(false);
        add(result);

        addBtn = new JButton("Add");
        subBtn = new JButton("Subtract");
        mulBtn = new JButton("Multiply");
        divBtn = new JButton("Divide");

        addBtn.addActionListener(this);
        subBtn.addActionListener(this);
        mulBtn.addActionListener(this);
        divBtn.addActionListener(this);

        add(addBtn);
        add(subBtn);
        add(mulBtn);
        add(divBtn);

        setVisible(true);
    }

    public void actionPerformed(ActionEvent e) {
        try {
            double num1 = Double.parseDouble(input1.getText());
            double num2 = Double.parseDouble(input2.getText());
            double output = 0;

            if (e.getSource() == addBtn)
                output = num1 + num2;
            else if (e.getSource() == subBtn)
                output = num1 - num2;
            else if (e.getSource() == mulBtn)
                output = num1 * num2;
            else if (e.getSource() == divBtn)
                output = num2 != 0 ? num1 / num2 : Double.NaN;

            result.setText(String.valueOf(output));
        } catch (NumberFormatException ex) {
            result.setText("Invalid Input");
        }
    }

    public static void main(String args[]) {
        new SimpleCalculator();
    }
}
