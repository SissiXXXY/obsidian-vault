### General Flow

```
Mock Container -> Mock Client -> Mock Response

```
### Mock Container
Fake server running in Docker
In Ledger-Service: ModernTreasuryMockContainer
- Acts like api.moderntreasury.com
- Receives HTTP requests from your service
- Replaces the real external API

### Mock Client
Helper in the test code
In Ledger-Service: ModernTreasuryMockClient
- Programs the mock container
- Tells it how to respond
![[Pasted image 20260406114313.png|597]]
### Mock Response
The **actual fake response** returned to your service
ledger service → calls API → mock container → returns mock response

### Full Flow
1. Test starts mock container (fake server)

2. Test uses mock client:
   → "when X request comes, return Y response"

3. Ledger service makes HTTP call

4. Mock container receives it

5. Returns the mock response you defined

6. Service continues as if it was real

