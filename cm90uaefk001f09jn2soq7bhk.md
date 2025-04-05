---
title: "What is MVC?"
seoTitle: "What Is MVC"
seoDescription: "Discover MVC: A design pattern that separates concerns, organizing complex applications with Models, Views, and Controllers for efficient programming"
datePublished: Thu Apr 03 2025 04:12:04 GMT+0000 (Coordinated Universal Time)
cuid: cm90uaefk001f09jn2soq7bhk
slug: what-is-mvc
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1743653426209/fd9adf48-a7ec-49cb-be59-1605ecebf666.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1743653463299/2c22c4e1-71e1-4cc5-b310-8119da56c099.png
tags: mvc, csharp, aspnet-core

---

MVC is a software programming design pattern and stands for model, view, controller. It is used to achieve a separation of concerns, which makes it easier to organize and program complex applications.

* **Controller**: It listens for requests from the user and then takes those requests to interact with both the models and the views.
    
* **Model**: It is the data or information from the database that is being requested in order to display to the user.
    
* **View**: This is the graphic user interface (gui) or web pages that display information on the screen to the user.
    
For example, in my contact book application, the Contact Edit page displays to the user the information for a single contact on a page in the web browser. The **Edit** action will have the Contacts **Controller** query the database for the contact using the contact id number. If the id number is found, the contact is returned as a **Model** to the **View** where information is displayed on the web page.

```csharp
public class ContactsController : Controller
{
	// GET: Contacts/Edit/5
	[Authorize]
	public async Task<IActionResult> Edit(int? id)
	{
		if (id == null || _context.Contacts == null)
		{
			return NotFound();
		}

		string appUserId = _userManager.GetUserId(User);

		var contact = await _context.Contacts.Where(c => c.Id == id && c.AppUserID == appUserId)
						     .FirstOrDefaultAsync();

		if (contact == null)
		{
			return NotFound();
		}

		return View(contact);
	}
}
```

So, learning about MVC is simple to understand and easy to implement. Don’t forget to leave a comment below to add to the conversation.