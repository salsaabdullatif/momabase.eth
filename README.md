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
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract CrowdfundingGoal {
    uint256 public goal = 10 ether;
    uint256 public raised;

    function contribute() external payable {
        raised += msg.value;
    }

    function goalReached() external view returns (bool) {
        return raised >= goal;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract StakingDeposit {
    mapping(address => uint256) public staked;

    function stake() external payable {
        staked[msg.sender] += msg.value;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LockPeriod {
    mapping(address => uint256) public lockUntil;

    function lock(uint256 duration) external {
        lockUntil[msg.sender] = block.timestamp + duration;
    }

    function isLocked(address user) external view returns (bool) {
        return block.timestamp < lockUntil[user];
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LockPeriod {
    mapping(address => uint256) public lockUntil;

    function lock(uint256 duration) external {
        lockUntil[msg.sender] = block.timestamp + duration;
    }

    function isLocked(address user) external view returns (bool) {
        return block.timestamp < lockUntil[user];
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract NFTOperator {
    mapping(address => mapping(address => bool)) public isApprovedForAll;

    function setApprovalForAll(address operator, bool approved) external {
        isApprovedForAll[msg.sender][operator] = approved;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract SimpleTransfer {
    mapping(uint256 => address) public ownerOf;

    function transfer(uint256 tokenId, address to) external {
        require(ownerOf[tokenId] == msg.sender, "Not owner");
        ownerOf[tokenId] = to;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract RoyaltyInfo {
    uint256 public royaltyBps = 500; // 5%

    function setRoyalty(uint256 bps) external {
        royaltyBps = bps;
    }
}
