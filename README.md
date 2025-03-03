# GRAVAXTEST
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract GRAVAX is ERC20, Ownable {
    uint256 public constant MAX_SUPPLY = 10_000_000 * 10**18; // 10M max supply

    constructor(address initialOwner) ERC20("GRAVAX", "GRAV") Ownable(initialOwner) {
        _mint(initialOwner, 1_000_000 * 10**18); // Mint 1M tokens to owner
    }

    function ownerMint(address to, uint256 amount) public onlyOwner {
        require(totalSupply() + amount <= MAX_SUPPLY, "Max supply reached");
        _mint(to, amount);
    }
}
