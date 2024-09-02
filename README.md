Данные контракты жетона и минтера представляют из себя стандарный контракт жетона с возможностью у пользователя минтить себе жетоны при получении пермита от бекенда.

Все опкоды стандартны для жетона за исключением op::unlock.

# Интерфейс op::unlock
```
opcode: 32 bits
query_id: 64 bits
signature: 512 bit
cell:
    address (user's jetton wallet)
    amount: coins
    cell:
        opcode: 32 bits (internal_transfer)
        query_id: 64 bits
        jetton_amount: coins
        ...
cell:
    address (treasury's jetton wallet)
    amount: coins
    cell:
        opcode: 32 bits (internal_transfer)
        query_id: 64 bits
        jetton_amount: coins
        ...
nonce: 16 bits

# Пример подписи на nodejs
```
import { sign, mnemonicToWalletKey, KeyPair } from '@ton/crypto';
...
const mnemonic : string = "your mnemonic";
const key : KeyPair = await mnemonicToWalletKey(mnemonic.split(" "));
let toSign = beginCell()
    .endCell();
let signature = sign(toSign.hash(), privKey);
```