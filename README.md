Part B pass 3 out of 3 tests, screen shot is shown below

![image](https://github.com/user-attachments/assets/f29f3925-2d72-4e26-9e1d-4f7784b75144)



Part C

In addition to the Transparent and UUPS proxy patterns, one noteworthy alternative is the Beacon proxy. In this model, the implementation address is stored in a separate “Beacon” contract rather than in the proxy itself. When the proxy receives a function call, it first queries the Beacon for the current implementation address, then delegates all calls to that address. Upgrades become a matter of updating the implementation address inside the Beacon, which means multiple proxies can share the same Beacon and upgrade logic in tandem. This centralization of the implementation address in the Beacon can simplify versioning and coordination if many proxies rely on the same code.

Compared to the Transparent and UUPS proxies, the Beacon model centralizes the upgrade process into a single contract that holds the implementation address. In contrast, a Transparent or UUPS proxy typically keeps the implementation address within each proxy’s storage. While the Beacon design can make managing multiple proxies easier (since you only update the Beacon once), it introduces a single point of upgrade that affects all proxies linked to that Beacon. By contrast, UUPS and Transparent proxies allow for more granular upgrades, since each proxy can point to a different implementation if needed.
