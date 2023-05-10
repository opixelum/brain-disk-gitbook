# Proxy

## Definition

A proxy is a contract that delegates calls to another contract called the
implementation. During an upgrade, the address of the implementation in the
proxy contract is changed, so it will delegate calls to the new implementation. 
The implementation contract uses the storage of the proxy contract, thanks to
the `DELEGATECALL` opcode.

## Types of proxies

### Transparent

### UUPS

- Lightweight & versatile;
- Upgrades are handled by the **implementation**;
- Implemented **using** an
  [**ERC1967Proxy**](https://docs.openzeppelin.com/contracts/4.x/api/proxy#ERC1967Proxy)
  contract;
- Implementation needs to **inherit** from
  [**UUPSUpgradeable**](https://docs.openzeppelin.com/contracts/4.x/api/proxy#UUPSUpgradeable).
- If a **non UUPS compliant implementation** tries to upgrade a UUPS proxy, the
  upgrade will fail & it will **lock** the upgradeability of the proxy 
  **forever** (thanks to security mechanism described in
  [**EIP1822**](https://eips.ethereum.org/EIPS/eip-1822).

## Initialization

Since proxies hold the storage, implementations need to be initialized through
the proxy's delegatecall, and not with a constructor. If a constructor is used,
initialized data will be stored in the implementation contract, leading to
missing data when using the proxy.

## References

- [Proxies - OpenZeppelin Docs](https://docs.openzeppelin.com/contracts/4.x/api/proxy)
