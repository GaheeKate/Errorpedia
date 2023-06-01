## Error message 

A PHP Error was encountered
Severity: 8192

Message: Return type of CI_Session_database_driver::open($save_path, $name) should either be compatible with SessionHandlerInterface::open(string $path, string $name): bool, or the #[\ReturnTypeWillChange] attribute should be used to temporarily suppress the notice

----
## How it happened?

Error Encountered During the Migration of CI3 Code to a Newer LEMP Environment for Future Upgrade to CI4


--- Cause

## 
Return type of CI_Session_database_driver didnt match the expected return type of 'bool' specified in the SesstionHanderInterface.
Probably I happened becuse I used a different(newer) version of PHP.
----
## Solutions

I used this way. 
the #[\ReturnTypeWillChange] attribute should be used to temporarily suppress the notice
``` php
    #[\ReturnTypeWillChange]
	public function gc($maxlifetime)
	{
		// Prevent previous QB calls from messing with our queries
		$this->_db->reset_query();

		return ($this->_db->delete($this->_config['save_path'], 'timestamp < '.(time() - $maxlifetime)))
			? $this->_success
			: $this->_fail();
	}
```
