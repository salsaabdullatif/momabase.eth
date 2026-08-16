// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract DutchStyle {
    uint256 public startPrice = 1 ether;
    uint256 public startTime = block.timestamp;

    function currentPrice() external view returns (uint256) {
        uint256 elapsed = block.timestamp - startTime;
        if (elapsed >= 1 days) return 0;
        return startPrice - (startPrice * elapsed / 1 days);
    }
}
