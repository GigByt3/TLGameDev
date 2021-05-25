# Unit Testing in C#

  This is a comprehensive guide on how to write and run unit Tests in C#.
  
# Writing a Unit Test

  The purpouse of a Unit Test is to run all methods of a class and to test that their returns match what would be expected. For example a Unit Test for an addition method might look as follows:
  
```
public int addition(int a, int b)
{
  return a + b
}

//Unit Test:

private bool testAddition()
{
  if(addition(2, 2) == 4)
  {
    return true;
  }
  return false;
}
```

  Now the principle of Unit tests...
