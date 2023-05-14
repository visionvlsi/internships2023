
Randomisation Functions
As the name suggests, these functions generate a random number. They are mainly used in testbench to create random test vectors.

$random
This function generates a random 32bit signed number.

$urandom
This function generates a 32bit random unsigned number.

$urandom_range
This function also generates a 32-bit random unsigned number but inside the range mentioned.

Example
```
module random_demo;
    reg [31:0] a, b;
    integer c;
    initial begin
        repeat(10) begin
            a = $urandom();
            b = $urandom_range(1, 8);
            c = $random();
            $display("a = %0d,\t\t\tb = %0d,\t\t\tc = %0d", a, b, c);
        end
    end
endmodule
```
