# Project Architecture

The following is a lesson plan outline for teaching about project architecture eith a focus on the tenants of Modular Design.

# Modular Design: A study in peace of mind.

Without architecture, just sitting down and making a project of any signifiant size is practically impossible. this is because of a certain phenomenon called **Technical Debt**. Practically Technical Debt is the proscess by which a project will accumulate hacky workarounds and fragile fixes that eventuaally break under evolving use cases and are increasingly hard to fix. However, with robust architecture you can cut these problems off at the pass and fix bugs much more easily.
  So, to begin, what is **Modular Design**? Well, the practice behind it is that you break down a large and complex project into smalller more manageable peices that are largey seperate from eachother. This would be like replacing the craftsman who was responsible for each individual peice of making a product, with an assembly line making each peice individually and having them all put together by a larger proscess. For example instead of writing one script to parse data out of a csv into a usable array, organize its peices and print them to a UI element, you would write one script to parse the data into an array, one script to seperate out important information, and one more to print that information out. 
```
class csvToUI
{
  private string csvInformation = Resources.Load("Assets/Resources/csvInfo");;
  
  private void OnAwake()
  {
    PrintCsv();
  }
  
  public void PrintCsv()
  {
    //Prints csvInformation onto a UI
  }
}
```

vs

```
public static class csvParser
{
  public static string[][] parseData(string csvInfo)
  {
    // Parse Logic goes here.
  }
}

class conversationManager
{
  private string csvInformation = Resources.Load("Assets/Resources/csvInfo");
  private string[][] dialougeInformation;
  
  private void OnAwake()
  {
    dialougeInformation = csvParser.parseData(csvInformation);
  }
  
  public string[] DialougeInformation(int index)
  {
    // Returns specific information from an index in dialougeInformation
  }
}

class UIPrinter
{
  private conversationManager convoManager;

  private void OnAwake()
  {
    convoManager = new conversationManager();
    printDialouge(convoManager.DialougeInformation(0));
  }
  
  public printDialouge(string[] information)
  {
    // Prints information to a UI element
  }
}
```
  Now the advantages of this system are as follows:
  
  - **Unit Testing**
  - **Modularity and Reusability**
  - **Ease of access for development by a larger team**
