# Expense-Tracker
This is a Expense Tracker website
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Expense Tracker</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .container {
            width: 300px;
            margin: 0 auto;
            text-align: center;
        }
        input[type="text"], input[type="number"], input[type="submit"] {
            margin-bottom: 10px;
            width: 100%;
            padding: 5px;
            box-sizing: border-box;
        }
        #expenses-list {
            text-align: left;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Expense Tracker</h2>
    <form id="expense-form">
        <input type="text" id="expense-name" placeholder="Expense Name" required>
        <input type="number" id="expense-amount" placeholder="Amount ($)" required>
        <input type="submit" value="Add Expense">
    </form>
    <h3>Expenses</h3>
    <ul id="expenses-list"></ul>
    <p>Total Expenses: $<span id="total-expenses">0</span></p>
</div>

<script>
    document.addEventListener('DOMContentLoaded', function() {
        const expenseForm = document.getElementById('expense-form');
        const expensesList = document.getElementById('expenses-list');
        const totalExpenses = document.getElementById('total-expenses');
        let total = 0;

        expenseForm.addEventListener('submit', function(event) {
            event.preventDefault();

            const expenseName = document.getElementById('expense-name').value;
            const expenseAmount = parseFloat(document.getElementById('expense-amount').value);

            if (expenseName && !isNaN(expenseAmount)) {
                total += expenseAmount;
                totalExpenses.textContent = total.toFixed(2);

                const listItem = document.createElement('li');
                listItem.textContent = `${expenseName}: $${expenseAmount.toFixed(2)}`;
                expensesList.appendChild(listItem);

                document.getElementById('expense-name').value = '';
                document.getElementById('expense-amount').value = '';
            } else {
                alert('Please enter valid expense name and amount!');
            }
        });
    });
</script>

</body>
</html>
