# Integrating the system into your code
***IMPORTANT! Don't forget to add the QuestsManager.cs script on scene!***
****

## Namespace
To use the system code, you need to include the namespace
```c#
    using QuestsSystem;
```

## Quest activation
Quest activation occurs through a call to QuestsManager.
```c#
	QuestsManager.Instance.AddQuest(QuestsNames.YourQuest);
```

After creating/deleting/modifying a quest through the editor, it automatically creates the enum list with all quests in the project:
```c#
	public enum QuestsNames
    {
        QuestOne,
        QuestTwo
    }
```

## Quest progress

If you have logic in the quest that needs to be updated after any action.
```c#
    QuestsManager.Instance.UpdateQuestProgress(QuestsNames.YourQuest);
```

## Quest complete/remove

If the quest has been completed
```c#
    QuestsManager.Instance.RemoveQuest(QuestsNames.YourQuest, true);
```

If you want to remove a quest from the list without calling OnComplete
```c#
    QuestsManager.Instance.RemoveQuest(QuestsNames.YourQuest, false);
```