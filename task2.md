Interface Segregation Principle (ISP) is the main design principle compromised here, as the Payment class should not be forced to depend on methods it does not use. However, it does because it has both bank operations and loan operations in one interface. Because of this, LoanPayment has to implement initiatePayments(), which isn't related to it. BankPayment is forced to implement intiateLoanSettlement() and initiateRePayment which it doesn't support. This also breaks the Liskov Substitution Principal as the code holding a Payment reference cannot safely these methods and will throw the UnsupportedOperationException if you use the non-supported methods

To fix it, we should split Payment into smaller, role-specific interfaces so each class only implements what it actually supports. Something like:

java
public interface Payment {
Object status();
}

public interface BankPayable extends Payment {
void initiatePayments();
}

public interface LoanPayable extends Payment {
void intiateLoanSettlement();
void initiateRePayment();
}

Then have LoanPayment implements LoanPayable, BankPayment implements BankPayable to fix the ISP and LSP issues.
