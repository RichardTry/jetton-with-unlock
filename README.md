Данные контракты жетона и минтера представляют из себя стандарный контракт жетона с возможностью у пользователя минтить себе жетоны при получении пермита от бекенда.

Все опкоды стандартны для жетона за исключением op::unlock.

# Интерфейс op::unlock
```
opcode: 32 bits
query_id: 64 bits
signature: 512 bit
to_address: address
amount: coins
treasury: address
amount_to_burn: coins
nonce: 16 bits
```

# Пример подписи на nodejs
```
import { sign } from '@ton/crypto';
...
let toSign = beginCell()
    .endCell();
let signature = sign(toSign.hash(), privKey);
```