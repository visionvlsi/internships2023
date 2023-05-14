#### Break
Break statement is a quite common keyword in C, which helps to come out of a loop when some condition is met. Let’s see how we can emulate break in Verilog. In below code, a counter is implemented which stops counting when its value becomes 4. An infinite loop is used inside a count block and when the condition is met, the code disables the count block inside which it is present. Thus, the program comes out of the loop and executes the remaining statements.

We can have multiple blocks inside the initial or always block as defined in below example. Begin and end can be compared to the {} we use in many programming language. It binds multiple statement in a single block. Thus, with initial or always block we use begin and end if there are multiple statements. But it doesn’t mean that we cannot declare multiple blocks inside it.
```
module break_demo;
    reg [3:0] a;
    initial begin
        a = 0;
        begin: count 
            forever 
            begin
                a = a + 1;
                $display("a = %0d", a);
                if (a > 3) 
                    disable count; 
            end
        end
        $display("Terminated Loop");
    end
endmodule
```
```
Output
# a = 1
# a = 2
# a = 3
# a = 4
# Terminated Loop
```

#### Continue
Continue statement is another common keyword in C. This is used to skip certain iterations of the loop when some condition is met. In simple words, whenever a condition is met it will not execute the remaining statements in the loop and go to next loop. Lets see how we can emulate continue in Verilog.
The code given below, prints the value of i if it is not divisible by 3. Whenever the condition is met it disables the count block. Thus, statements present after the disable statement will not execute and the program will move to the next iteration. In this way continue is emulated in Verilog.
```
module continue_demo;
    reg [3:0] i;
    initial begin
        i = 0;
        begin
            for(i=1; i<=10; i=i+1) 
            begin: count 
                if (i % 3 == 0) 
                    disable count; 
                $display("i = %0d", i); 
            end
        end
        $display("Terminated Loop");
    end
endmodule
```
```
Output
# i = 1
# i = 2
# i = 4
# i = 5
# i = 7
# i = 8
# i = 10
# Terminated Loop
```
