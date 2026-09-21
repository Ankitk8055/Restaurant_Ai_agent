### Agent Flow 

The restaurant order management agent is built using LangGraph. The LLM acts as the central decision-making node and controls the workflow based on the current order status and available retries.

1. User provides a food order.
2. The LLM extracts the dish name and quantity.
3. `order_confirm` checks the requested item against the menu and available stock.
4. If the order is valid, it moves to the `cook` node.
5. Cooking has a 60% success probability and can be retried based on the retry counter.
6. After successful cooking, the order moves to `serve`.
7. Serving also has a 60% success probability and can trigger a re-cook + re-serve.
8. The LLM communicates the current status to the customer at each stage.
9. The workflow ends when the order is completed or the retry limits are exhausted.
