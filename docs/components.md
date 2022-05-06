# Creating custom components for the system
This example will show the creation of a trigger to activate the quest
****

## Create a new class
You can create whatever you want, but in this example it will be QuestTrigger.cs

## Quest info
Add a variable where we will store information about the quest that will call this component
```c#
    [SerializeField] private QuestsNames questName; //Set the required quest from inspector
```

## Trigger
Since this is a trigger, we add the standard unity method
```c#
    private void OnTriggerEnter(Collider other)
    {
        if (other.gameObject.tag == "Player")
        {
            gameObject.SetActive(false); //self-disabling
        }
    }
```

## Parameters
Parameters for defining the trigger type
```c#
    private enum TriggerType { Accept, Update, Complete }
    [SerializeField] private TriggerType triggerType;
```
## Quest action
We check for the type of trigger and select the desired action with the quest
```c#
    private void OnTriggerEnter(Collider other)
    {
        if (other.gameObject.tag == "Player")
        {
            //Perform the desired action depending on the selected type
            switch (triggerType)
            {
                case TriggerType.Accept:
                    QuestsManager.Instance.AddQuest(questName);
                    break;
                case TriggerType.Update:
                    QuestsManager.Instance.UpdateQuestProgress(questName);
                    break;
                case TriggerType.Complete:
                    QuestsManager.Instance.RemoveQuest(questName, true);
                    break;
            }
    
            gameObject.SetActive(false); //self-disabling
        }
    }
```