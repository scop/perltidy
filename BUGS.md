# Perltidy open BUGS and LIMITATIONS

You can help perltidy evolve into a better program.  If you think you
have hit a bug or weird behavior, or have a suggested improvement,
please send a note to perltidy at users.sourceforge.net.

This file only lists open bugs.  For bugs which have been fixed, 
see the ChangeLog.  

## The --extrude and --mangle options can produce code with syntax errors

The --extrude tries to put as many newlines in the formatted code as possible.
The --mangle tries to remove as many newlines as possible.  These options are
very useful for stress testing perltidy (and Perl) but not so much for normal
formatting.  Occasionally they will produce code which Perl considers to have a
syntax error.  These problems often involve code where Perl is having to guess
the tokenization based on whitespace.  The given/when and switch/case
statements are also particularly vulnerable to unusual line breaks and
whitespace.  This type of error should not normally occur in practice, but if
it does it should be easy to fix the problem by rerunning perltidy with more
normal parameters or by manually changing whitespace or newlines. 

## The Pod:Html module has some bugs

For the most part Pod::Html works very well and is very convenient because
it part of the standard Perl distribution.  But for example the following line

    =item B<< <Deck> = Session->new_cflt_deck; >>

which uses double brackets to contain single brackets does not render correctly.

## Two iterations are sometimes needed

Usually the code produced by perltidy on the first pass does not change if it
is run again, but sometimes a second pass will produce some small additional
change.  This mainly happens if a major style change is made, particularly when
perltidy is untangling complex ternary statements. Use the iteration parameter
**-it=2** if it is important that the results be unchanged on subsequent passes,
but note that this doubles the run time.

## Latest Bug and Wishlist at CPAN:

For the latest list of bugs and feature requests at CPAN see:

https://rt.cpan.org/Public/Dist/Display.html?Name=Perl-Tidy
