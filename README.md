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
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract OfferSystem {
    mapping(uint256 => uint256) public offers;

    function makeOffer(uint256 tokenId) external payable {
        offers[tokenId] = msg.value;
    }
}// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract WhitelistMint {
    bool public whitelistOnly = true;

    function setWhitelistOnly(bool enabled) external {
        whitelistOnly = enabled;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract RevealFlag {
    bool public revealed;

    function reveal() external {
        revealed = true;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract ContractURI {
    string public contractURI;

    function setContractURI(string calldata uri) external {
        contractURI = uri;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract OnChainMetadata {
    bool public onChainMetadata;

    function enableOnChain() external {
        onChainMetadata = true;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract OnChainMetadata {
    bool public onChainMetadata;

    function enableOnChain() external {
        onChainMetadata = true;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract DailyClaim {
    mapping(address => uint256) public lastClaim;

    function claim() external {
        require(block.timestamp >= lastClaim[msg.sender] + 1 days, "Too early");
        lastClaim[msg.sender] = block.timestamp;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract ReferralCode {
    mapping(address => string) public codeOf;

    function setCode(string calldata code) external {
        codeOf[msg.sender] = code;
    }
}
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LeaderboardScore {
    mapping(address => uint256) public score;

    function setScore(uint256 newScore) external {
        score[msg.sender] = newScore;
    }
}
