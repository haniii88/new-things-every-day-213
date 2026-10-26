```javascript
function dailyLog213() {
  const budget = [
    { category: "Food", limit: 400, spent: 320 },
    { category: "Transport", limit: 150, spent: 175 },
    { category: "Entertainment", limit: 100, spent: 85 },
    { category: "Shopping", limit: 200, spent: 240 },
    { category: "Utilities", limit: 250, spent: 210 },
  ];

  const totalBudget = budget.reduce(
    (sum, item) => sum + item.limit,
    0
  );

  const totalSpent = budget.reduce(
    (sum, item) => sum + item.spent,
    0
  );

  const exceeded = budget.filter(
    item => item.spent > item.limit
  );

  console.log("=== Monthly Budget Report ===");
  console.log(`Total Budget: $${totalBudget}`);
  console.log(`Total Spent: $${totalSpent}`);
  console.log(`Remaining: $${totalBudget - totalSpent}`);
  console.log(`Over-Budget Categories: ${exceeded.length}`);

  console.log("\n=== Category Breakdown ===");

  budget.forEach(item => {
    const difference = item.limit - item.spent;
    const status = difference < 0 ? "⚠️ Over Budget" : "✅ Within Budget";

    console.log(
      `${item.category}: $${item.spent}/$${item.limit} — ${status}`
    );
  });

  if (exceeded.length > 0) {
    console.log("\n=== Categories to Review ===");

    exceeded.forEach(item => {
      console.log(
        `${item.category}: $${item.spent - item.limit} over budget`
      );
    });
  }
}

dailyLog213();
```
