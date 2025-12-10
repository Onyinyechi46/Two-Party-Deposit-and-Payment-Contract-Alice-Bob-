# Two-Party-Deposit-and-Payment-Contract-Alice-Bob-
This contract requires Alice to first deposit 1000 units. After she does, Bob must deposit 500 units. Once both deposits are made, the contract automatically pays Bob 1000 units from Alice’s account and then closes. If either party fails to deposit before the deadline, the contract ends without executing the payment.
# Two-Party Deposit and Payment Contract (Alice ↔ Bob)

## Contract Description

This Marlowe contract follows a simple three-step flow involving Alice and Bob. First, the contract waits for **Alice** to deposit **1000 units** into her account. After Alice deposits, the contract then requires **Bob** to deposit **500 units** into his account. Once both parties have made their required deposits, the contract automatically transfers **1000 units** from Alice’s account to Bob and then closes. If either Alice or Bob fails to make their deposit before the deadline (`1765366466560`), the contract stops immediately without executing the payment.

## Contract Snippet

```marlowe
Case
  (Deposit
      (Role "Alice")
      (Role "Alice")
      (Token "" "")
      (Constant 1000)
  )
  (When
      [ Case
          (Deposit
              (Role "Bob")
              (Role "Bob")
              (Token "" "")
              (Constant 500)
          )
          (Pay
              (Role "Alice")
              (Party (Role "Bob"))
              (Token "" "")
              (Constant 1000)
              Close
          )
      ]
      1765366466560
      Close
  )
