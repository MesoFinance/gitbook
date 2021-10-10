---
description: Verify with our deployed contracts
---

# Farm Security Measures

## Security Measures taken in the fMESO token contract:

* Only the masterchef can mint succeeding tokens aside from the pre-minted ones for initial liquidity:

```
    // @dev Throws if called by any account other than the Masterchef.
    modifier onlyMasterchef() {
        require(msg.sender == masterchef, "Caller is not the Masterchef");
        _;
    }
    
    /// @notice Creates `_amount` token to `_to`. Must only be called by the owner (MasterChef).
    function mint(address _to, uint256 _amount) public onlyMasterchef {
        _mint(_to, _amount);
    }
```

## Security Measures taken in the Masterchef contract:

* fMeso address is made immutable:

```
 // The fMESO TOKEN!
    fMeso public immutable token;
```

* Deposit fees are capped to 4%:

```
    function add(uint256 _allocPoint, IERC20 _lpToken, uint16 _depositFeeBP, bool _withUpdate) external onlyOwner nonDuplicated(_lpToken) {
        // valid ERC20 token
        _lpToken.balanceOf(address(this));

        require(_depositFeeBP <= 400, "add: invalid deposit fee basis points");
        
        
    function set(uint256 _pid, uint256 _allocPoint, uint16 _depositFeeBP, bool _withUpdate) external onlyOwner {
        require(_depositFeeBP <= 400, "set: invalid deposit fee basis points");
```

* Pools account for deflationary tokens:

```
 // Deposit LP tokens to MasterChef for fMESO allocation.
    function deposit(uint256 _pid, uint256 _amount) external nonReentrant {
        PoolInfo storage pool = poolInfo[_pid];
        UserInfo storage user = userInfo[_pid][msg.sender];
        updatePool(_pid);
        if (user.amount > 0) {
            uint256 pending = user.amount.mul(pool.accfMesoPerShare).div(1e18).sub(user.rewardDebt);
            if (pending > 0) {
                safeMesoTransfer(msg.sender, pending);
            }
        }
        if (_amount > 0) {
            uint256 balanceBefore = pool.lpToken.balanceOf(address(this));
            pool.lpToken.safeTransferFrom(address(msg.sender), address(this), _amount);
            _amount = pool.lpToken.balanceOf(address(this)) - balanceBefore;
```
