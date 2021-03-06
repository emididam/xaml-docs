---
title: Getting Started
page_title: Getting Started
description: Getting Started
slug: chat-getting-started
tags: getting,started
published: True
position: 0
---

# Getting Started

This topic will guide you through the process of creating a sample application containing __RadChat__.

* [Assembly References](#assembly-references)
* [Adding RadChat to the Project](#adding-radchat-to-the-project)
* [Adding Authors to RadChat](#adding-authors-to-radchat)

## Assembly References

* __Telerik.Windows.Controls__
* __Telerik.Windows.Controls.Input__
* __Telerik.Windows.Controls.Navigation__
* __Telerik.Windows.Controls.ConversationalUI__

## Adding RadChat to the Project

Before proceeding with adding __RadChat__ to your project, make sure the required assembly references are added to the project. 

You can add __Conversational UI__ manually by writing the XAML code in __Example 1__. You can also add the control by dragging it from the Visual Studio Toolbox and dropping it over the XAML view.

#### __[XAML] Example 1: Adding RadChat in XAML__

{{region xaml-chat-getting-started_0}}
	<telerik:RadChat />
{{endregion}}

Running the application at this state will result in an empty chat.

#### __Figure 1: The Empty Chat Generated by the Code in Example 1__

![Empty RadChat](images/RadChat_GettingStarted_01.png)

## Adding Authors to RadChat

Two authors will be defined for this example. Note, that the __CurrentAuthor__ property of __RadChat__  must be set.

#### __[C#] Example 3: Adding Authors to RadChat__

{{region cs-chat-getting-started_2}}
	public partial class MainWindow : Window
    {
        private Author currentAuthor;
        private Author otherAuthor;

        public MainWindow()
        {
            InitializeComponent();

            currentAuthor = new Author("1") { Name = "Peter" };
            otherAuthor = new Author("2") { Name = "Steven" };
            this.chat.CurrentAuthor = currentAuthor;
        }
    }
{{endregion}}

## Handling the Sent Message

The user's input can be handled by hooking up to the __SendMessage__ event of __RadChat__. The event arguments are of type __RoutedEventArgs__ which are extended by the __Message__ property.

#### __[C#] Example 4: Subscribing to the SendMessage event__

{{region cs-chat-getting-started_3}}
	 private void Chat_SendMessage_(object sender, SendMessageEventArgs e)
        {
            var author = e.Message.Author;
            if (author == this.chat.CurrentAuthor)
            {
                this.chat.AddMessage(this.currentAuthor, (e.Message as TextMessage).Text);
                this.chat.AddMessage(this.otherAuthor, (e.Message as TextMessage).Text);

                e.Handled = true;
            }
        }
{{endregion}}

This setup will have the following result.

#### __Figure 2: RadChat with Messages__

![RadChat with Messages](images/RadChat_GettingStarted_02.png)

## See Also

* [Overview]({%slug chat-overview%})
* [Messages Overview]({%slug chat-items-messages-overview%})











