- **Perl** is a programming language created by Larry Wall in 1987 to easily process textual information. This interpreted language is inspired by the control and printing structures of the C language, but also by the scripting languages sed, awk and shell.
-
- ### Arrow operator ( -> )
	- Used for [dereferencing](http://www.perlmeme.org/howtos/using_perl/dereferencing.html) a Variable or a Method from a class or an object
	- ```perl 
	  #!/usr/local/bin/perl
	  
	  use strict;
	  use warnings;
	  
	  # reference to array
	  my $arr1 = [4,5,6];
	  
	  # array inside array
	  my $arr2 = [4,5,[6,7]];
	  
	  # reference to hash
	  my $has1 = {'a'=>1,'b'=>2};
	  
	  # hash inside hash
	  my $has2 = {'a'=>1,'b'=>2,'c'=>[1,2],'d'=>{'x'=>3,'y'=>4}};
	  
	  print "$arr1->[0]\n";
	  print "$arr2->[1]\n";
	  print "$arr2->[2][1]\n";
	  print "$has1->{'b'}\n";
	  print "$has2->{'a'}\n";
	  
	  print $has2->{'d'}->{'x'},"\n";
	  print "$has2->{'d'}->{'x'}\n"; # same
	  
	  print $has2->{'c'}->[0],"\n";
	  print "$has2->{'c'}->[0]\n"; # same
	  ```
	  
	  ```bash 
	  # Output
	  4
	  5
	  7
	  2
	  1
	  3
	  3
	  1
	  1
	  ```
-
- ### Raspberry Pi GPIO pins
	- [RPi::Pin](https://metacpan.org/pod/RPi::Pin) - Access and manipulate Raspberry Pi GPIO pins
	- ```perl
	  use RPi::Pin;
	  use RPi::Const qw(:all);
	   
	  my $pin = RPi::Pin->new(5);
	   
	  $pin->mode(INPUT);
	  $pin->write(LOW);
	   
	  $pin->set_interrupt(EDGE_RISING, 'main::pin5_interrupt_handler');
	   
	  my $num = $pin->num;
	  my $mode = $pin->mode;
	  my $state = $pin->read;
	   
	  print "pin number $num is in mode $mode with state $state\n";
	   
	  sub pin5_interrupt_handler {
	      print "in interrupt handler\n";
	  }
	  ```