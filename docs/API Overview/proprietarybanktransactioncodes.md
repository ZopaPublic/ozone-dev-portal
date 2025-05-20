# Proprietary Bank Transaction Codes

The proprietary bank transaction codes returned vary between Zopa products. Details of these are outlined below:


| Product        | Code                         | Definition       |
|----------------|------------------------------|------------------|
|Credit Card     |BALANCE_TRANSFER              |Balance transfer linked to an account |
|Credit Card     |BALANCE_TRANSFER_FEE          |Fee on a balance transfer |
|Credit Card     |BALANCE_TRANSFER_REFUNDED     |Refund of a balance transfer |
|Credit Card     |BALANCE_TRANSFER_FEE_REFUNDED |Refund of a balance transfer fee |
|Credit Card     |BALANCE_TRANSFER_INTEREST     |Interest on a balance transfer |
|Credit Card     |CASH_WITHDRAWAL               |Cash withdrawal made by the cardholder |
|Credit Card     |CASH_WITHDRAWAL_INTEREST      |Interest accrued on cash withdrawals |
|Credit Card     |CASH_WITHDRAWAL_FEE           |Fee charged on a cash withdrawal |
|Credit Card     |CASH_WITHDRAWAL_FEE_REFUNDED  |Refund of a fee charged on a cash withdrawal |
|Credit Card     |DISPUTE_REFUNDED              |Refund due to a dispute claim |
|Credit Card     |DISPUTE_REJECTED              |Dispute claim unsuccessful |
|Credit Card     |FEE_INTEREST                  |Interest on Fees |
|Credit Card     |FRAUD_REFUNDED                |Refund due to a fraud claim |
|Credit Card     |FRAUD_REJECTED                |Fraud claim unsuccessful |
|Credit Card     |GENERIC_ADJUSTMENT            |An adjustment or correction |
|Credit Card     |GOODWILL_PAYMENT              |Goodwill gesture |
|Credit Card     |INTEREST_REFUNDED             |Interest refund |
|Credit Card     |MISSED_PAYMENT_FEE            |Fee due to a missed payment |
|Credit Card     |MISSED_PAYMENT_FEE_REFUNDED   |Refund of a missed payment fee |
|Credit Card     |PURCHASE                      |A purchase made by the cardholder |
|Credit Card     |PURCHASE_INTEREST             |Interest on purchases made by the cardholder |
|Credit Card     |REFUND                        |A refund |
|Credit Card     |REPAYMENT                     |Repayment made the cardholder |
|Credit Card     |REPAYMENT_UNAPPLIED           |Reversal of a repayment made by the cardholder |
|Credit Card     |WRITE_OFF                     |A write-off |
|Current Account     |AUTHORISATION_APPROVED    |A card payment authorisation that was approved |
|Current Account     |AUTHORISATION_DECLINED |A card payment authorisation that was declined |
|Current Account     |AUTHORISATION_REVERTED |A card payment that was reverted |
|Current Account     |AUTHORISATION_INCREASE |An increase to a card authorisation requested by a merchant |
|Current Account     |AUTHORISATION_INCREASE_APPROVED |An increase in the authorisation hold on a card that was approved |
|Current Account     |AUTHORISATION_INCREASE_REVERTED |An increase in the authorisation hold on a card that was approved but subsequently declined |
|Current Account     |AUTHORISATION_INCREASE_DECLINED |An increase in the authorisation hold on a card that was declined |
|Current Account     |AUTHORISATION_ADVICE |A reduction in the authorisation amount on a card provided by the merchant |
|Current Account     |AUTHORISATION_REDUCED |A reduction in the authorisation amount on a card by the merchant, provided as a delta amount |
|Current Account     |AUTHORISATION_REVERSAL_ISSUER_EXPIRATION |A reversal generated when an authorised payment is not cleared by the merchant before expiration |
|Current Account     |AUTHORISATION_REVERSAL |A decrease in the authorisation amount on a card when the final transaction amount is less than the initial authorisation |
|Current Account     |PURCHASE_CLEARING |A purchase or cash withdrawal that has been cleared |
|Current Account     |AUTH_ADJUSTMENT_FOR_PURCHASE |An adjustment to clear any pending authorisation amount immediately after a purchase clearing |
|Current Account     |PURCHASE_CLEARING_NO_AUTH |A purchase or cash withdrawal that was cleared without any prior authorisation |
|Current Account     |MERCHANT_REFUND |Refund issued by the merchant after the original transaction has cleared |
|Current Account     |OCT_Authorisation_Approved |An acknowledgement of an approved authorisation |
|Current Account     |OCT_Authorisation_Reverted |An authorisation that was reverted after being initially approved |
|Current Account     |OCT_Authorisation_Reverted_Timeout | An authorisation that was reverted after being initially approved |
|Current Account     |OCT_Clearing |A transaction that has been cleared |
|Current Account     |OCT_Authorisation_Decline |An authorisation that was declined |
|Current Account     |OCT_Authorisation_Reversed |A merchant reversal of an authorisation |
|Current Account     |OCT_Authorisation_Reversed_Issuer_Expiration |A merchant reversal of an authorisation due to issuer expiration |
|Current Account     |FASTER_PAYMENT_IN |An inbound faster payment |
|Current Account     |FASTER_PAYMENT_IN_AUTHORISATION |An inbound faster payment |
|Current Account     |FASTER_PAYMENT_IN_EXTERNALLY_HELD |An inbound faster payment that is being held |
|Current Account     |FASTER_PAYMENT_IN_ADDITIONAL_SCREENING |An inbound faster payment that is being held |
|Current Account     |FASTER_PAYMENT_IN_SCREENING_FAILED |An inbound faster payment that was rejected |
|Current Account     |FASTER_PAYMENT_IN_RETURN |An inbound faster payment returned by the receiving bank |
|Current Account     |FASTER_PAYMENT_OUT_AUTHORISATION_APPROVED |An outbound faster payment authorisation that was approved |
|Current Account     |FASTER_PAYMENT_OUT_AUTHORISATION_DECLINED  |An outbound faster payment authorisation that was declined |
|Current Account     |FASTER_PAYMENT_OUT_AUTHORISATION_APPROVED_RELEASED |A failed outbound faster payment |
|Current Account     |FASTER_PAYMENT_OUT_ADDITIONAL_SCREENING |A outbound faster payment undergoing  screening |
|Current Account     |FASTER_PAYMENT_OUT_FAILED |A failed outbound faster payment |
|Current Account     |FASTER_PAYMENT_OUT_REJECTED |A failed outbound faster payment |
|Current Account     |FASTER_PAYMENT_OUT_SCREENING_FAILED |A failed outbound faster payment |
|Current Account     |FASTER_PAYMENT_OUT_SENT |A successful outbound faster payment |
|Current Account     |DIRECT_DEBIT_REQUEST |A direct debit payment |
|Current Account     |DIRECT_CREDIT_REQUEST |A direct credit payment |
|Current Account     |INTEREST_APPLIED |Monthly interest payment |
|Current Account     |FEEDBACK_PAYMENT  |A thank you payment for customers providing feedback |
|Current Account     |INTEREST_INCREASE_ADJUSTMENT  |An interest adjustment |
|Current Account     |ADJUSTMENT_INCREASE_COMMITTED  |An adjustment or correction |
|Current Account     |ADJUSTMENT_DECREASE_COMMITTED  |An adjustment or correction |
|Current Account     |CARD_ADJUSTMENT_INCREASE_PENDINGOUT |An adjustment or correction |
|Current Account     |CARD_ADJUSTMENT_REVERSE_PENDINGOUT |An adjustment or correction |
|Current Account     |PAYMENT_ADJUSTMENT_INCREASE_PENDING |An adjustment or correction |
|Current Account     |PAYMENT_ADJUSTMENT_REVERSE_PENDING |An adjustment or correction |
|Current Account     |POO_RELEASE_FUND  |An overseas payment |
|Current Account     |MANUAL_PAYMENT_OUT  |An outbound payment |
|Current Account     |CASHBACK_BONUS  |A cashback bonus payment |
|Current Account     |APPLE_PAY_INCENTIVE  |Apple Pay bonus payment |
|Current Account     |OFP_BANK_ERROR_REFUND  |A refund |
|Current Account     |MANUAL_FEE |A fee charged to the customer |
|Current Account     |CARD_DISPUTE_REFUND  |A refund |
|Current Account     |CARD_FRAUD_REFUND  |A refund |
|Current Account     |Interest_Refund  |A refund |
|Current Account     |Interest_Refund_Reversal  |A refund reversal |
|Current Account     |CARD_DISPUTE_REFUND_NONRECOVERABLE |A refund |
|Current Account     |CARD_FRAUD_REFUND_NONRECOVERABLE |A refund |
|Current Account     |CARD_DISPUTE_REFUND_REVERSAL  |A refund reversal |
|Current Account     |CARD_FRAUD_REFUND_REVERSAL  |A refund reversal |
|Current Account     |CARD_DISPUTE_ZOPA_LOSS |tbc |
|Current Account     |CARD_FRAUD_ZOPA_LOSS |tbc |
|Current Account     |CARD_DISPUTE_FAIL |tbc |
|Current Account     |CARD_FRAUD_FAIL |tbc |
|Current Account     |CARD_DISPUTE_FINAL_WIN |tbc |
|Current Account     |OFP_APP_FRAUD_REFUND  |A refund |
|Current Account     |OFP_UNAUTHORISED_REFUND   |A refund |
|Current Account     |DIRECT_DEBIT_REFUND   |A refund |
|Current Account     |DIRECT_DEBIT_REFUND_REVERSAL   |A refund reversal |
|Current Account     |DIRECT_DEBIT_ZOPA_LOSS   |tbc |
|Current Account     |IFP_APP_FRAUD_DEDUCTION   |A deduction |
|Current Account     |IFP_APP_FRAUD_DEDUCTION_REVERSAL   |A deduction reversal |
|Current Account     |GOODWILL_PAYMENT   |Goodwill gesture |
|Current Account     |MANUAL_FASTER_PAYMENT_OUT_RETURN   |tbc |
|Current Account     |INTEREST_REFUND   |A refund |
|Current Account     |INTEREST_REFUND_REVERSAL    |A refund reversal |
