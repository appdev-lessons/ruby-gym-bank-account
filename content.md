# Ruby Gym: Bank Account

Write a class called `BankAccount` that represents a simple bank account. The class should allow users to deposit, withdraw, and check their balance.

Like the Todo List, this is practice for [Bridge to Rails: Defining and using Classes](/lessons/573-classes-in-ruby): an `initialize` method, an instance variable, and instance methods that read and change it.

## Objectives

### 1. Create the `BankAccount` Class:
- In `initialize`, set an instance variable `@balance` to `0`.

### 2. Add a `deposit` Method:
- Define a method `deposit` that takes a single argument, `amount`.
- This method should add the `amount` to the `@balance`.
- If the amount is negative or zero, print `"Invalid deposit amount"` and leave the balance alone.

### 3. Add a `withdraw` Method:
- Define a method `withdraw` that takes a single argument, `amount`.
- This method should subtract the `amount` from the `@balance`.
- If the amount is greater than the balance, print `"Insufficient funds"` and do not change the balance.
- If the amount is negative or zero, print `"Invalid withdrawal amount"` and do not change the balance.

### 4. Add a `check_balance` Method:
- Define a method `check_balance` that returns the current balance.

## Tips
- Implement the `BankAccount` class and its methods as described. (You can leave the method implementations empty at first)
- Try running in your own codespace
- Use `puts` statements for logging and debugging

## Exercise

**Note:** The tests below are expecting you to use `puts` rather than `pp` when you print out strings. So be sure to use `puts` in your code when printing those strings.

```ruby
# write your program below

account = BankAccount.new
account.deposit(100)
account.withdraw(30)
puts account.check_balance  # Should output 70

account.withdraw(100)       # Should print "Insufficient funds"
account.deposit(-50)        # Should print "Invalid deposit amount"
```
{: .codeblock #bank_account title="Bank Account" points="1"}

```ruby
describe "BankAccount" do
  it "initializes with a balance of 0" do
    account = BankAccount.new
    expect(account.check_balance).to eq(0)
  end
end
```
{: .codeblock-test #bank_account_test_1 for="bank_account" title="BankAccount initializes with a balance of 0" points="1"}

```ruby
describe "BankAccount" do
  it "allows deposits and updates balance correctly" do
    account = BankAccount.new
    account.deposit(100)
    expect(account.check_balance).to eq(100)
  end
end
```
{: .codeblock-test #bank_account_test_2 for="bank_account" title="BankAccount allows deposits and updates balance correctly" points="1"}

```ruby
describe "BankAccount" do
  it "rejects negative or zero deposits" do
    account = BankAccount.new
    expect { account.deposit(-50) }.to output("Invalid deposit amount\n").to_stdout
    expect(account.check_balance).to eq(0)
  end
end
```
{: .codeblock-test #bank_account_test_3 for="bank_account" title="BankAccount rejects negative or zero deposits" points="1"}

```ruby
describe "BankAccount" do
  it "allows withdrawals and updates balance correctly" do
    account = BankAccount.new
    account.deposit(100)
    account.withdraw(30)
    expect(account.check_balance).to eq(70)
  end
end
```
{: .codeblock-test #bank_account_test_4 for="bank_account" title="BankAccount allows withdrawals and updates balance correctly" points="1"}

```ruby
describe "BankAccount" do
  it "rejects withdrawals greater than balance" do
    account = BankAccount.new
    account.deposit(50)
    expect { account.withdraw(100) }.to output("Insufficient funds\n").to_stdout
    expect(account.check_balance).to eq(50)
  end
end
```
{: .codeblock-test #bank_account_test_5 for="bank_account" title="BankAccount rejects withdrawals greater than balance" points="1"}

```ruby
describe "BankAccount" do
  it "rejects negative withdrawals without changing the balance" do
    account = BankAccount.new
    account.deposit(50)
    expect { account.withdraw(-30) }.to output("Invalid withdrawal amount\n").to_stdout
    expect(account.check_balance).to eq(50)
  end
end
```
{: .codeblock-test #bank_account_test_6 for="bank_account" title="BankAccount rejects negative withdrawals without changing the balance" points="1"}

```ruby
describe "BankAccount" do
  it "rejects a deposit or withdrawal of zero" do
    account = BankAccount.new
    account.deposit(50)
    expect { account.deposit(0) }.to output("Invalid deposit amount\n").to_stdout
    expect { account.withdraw(0) }.to output("Invalid withdrawal amount\n").to_stdout
    expect(account.check_balance).to eq(50)
  end
end
```
{: .codeblock-test #bank_account_test_7 for="bank_account" title="BankAccount rejects a deposit or withdrawal of zero" points="1"}

---

- Approximately how long (in minutes) did this lesson take you to complete?
{: .free_text_number #time_taken title="Time taken" points="1" answer="any" }
