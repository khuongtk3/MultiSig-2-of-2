# MultiSig-2-of-2
MultiSig 2‑of‑2
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract MultiSig {
    address public a;
    address public b;

    constructor(address _b) {
        a = msg.sender;
        b = _b;
    }

    function withdraw(address payable to, uint256 amount) public {
        require(msg.sender == a || msg.sender == b, "Not signer");
        to.transfer(amount);
    }

    receive() external payable {}
}
