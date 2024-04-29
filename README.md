# pulse.ai
**Goal: Automating ERP Actions with LLMs**
Demo goal: 1) Purchase Order Automation with LLM, 2) LLM search and discussions about company data 

## Terminology
ERPs: Enterprise Resource Planning
  - manage accounting, procurement, project management, risk management, compliance, supplier information
PR: Purchase Request
PO: Purchase Order

## Current process
Currently, companies have a JIRA ticket (or similar) containing information about the purchase order. The supply chain analysts have to manually go in, comprehend the request, then enter it in the given purchase order form in the ERP. For the demo here is the information needing to be encoded in a mock ticket: Supplier, Quantity, Net Price,  Supplier, Part Number, Assignee, Priority, Description, and potential file attachment for CAD files, for example. We can mock all of this information, feel free to put nonsense in each field for now. 

Here's an example of a mini JIRA-like ticket containing the information we want in the order:
<img width="396" alt="Screenshot 2024-04-28 at 10 06 33 PM" src="https://github.com/ritvikp22/pulse.ai/assets/38197497/2817d160-b765-4f00-9181-deb40bc5be2c">

Also, here's an image of how SAP POs look (they're basically just forms in the ERP that are sent out to suppliers):
<img width="880" alt="Screenshot 2024-04-28 at 10 15 57 PM" src="https://github.com/ritvikp22/pulse.ai/assets/38197497/cd583ded-1a8f-4900-a0cc-0e9696feca93">
Also can reference this video on PO creation: https://www.youtube.com/watch?v=cqrmtDVdlqc&t=77s

## Further demo details
We want to build a demo ERP interface. We start with basic log in email/password. In the basic ERP UI, it should appear like the following:
<img width="833" alt="Screenshot 2024-04-28 at 10 24 55 PM" src="https://github.com/ritvikp22/pulse.ai/assets/38197497/dc0da09a-fa5f-4c85-96d5-a1dbad712cce">
The two tabs we care about are Tickets, and Purchase Orders (lowkey the other tab buttons can be useless). Tickets tab should list all the open tickets, preferably in Kanban format just like JIRA does it, completed tickets, and in progress tickets. (Not super important to fill them all in with fake data, understandably takes time)
The Purcahse order ticket should have past purchase orders listed, and a button to create a new PO. Upon clicking the button, a chat interface should open where the GPT will ask questions about which ticket #, clarifying questions, and then output the PO with the ability to then send to supplier. But basically what I think we would do is just pre-prompt with “make a purchase order w/ this exact format…” *Feel free to work with the UI/UX depending on what you think looks the best and most functional -- we can discuss in our daily standups.* 

The second main feature is a search functionality where the user has the ability to search the current company info (just POs, tickets) in this case, and chat with GPT about progress, what tickets need to be sent to suppliers, updates on payment/invoices, etc. This one seems bit hard but can be pretty rudimentary for demo. 

## Additional Resources
1. I mocked a basic ERP dashboard look - definitely need improvement but think this should be a good starting point in terms of frontend. 
<img width="1093" alt="Screenshot 2024-04-28 at 10 31 19 PM" src="https://github.com/ritvikp22/pulse.ai/assets/38197497/bf163403-edbb-4f13-a344-a678498fc434">
2. https://www.youtube.com/watch?v=2mDpe8RpcPA&pp=ygUac2FwIHB1cmNoYXNlIG9yZGVyIHByb2Nlc3M%3D


PO fields we're interested in:
```{
  "POs": [
    {
      "po_number": 248493,
      "inco_terms": "DDP",
      "quantity": 10,
      "unit": "Batch",
      "type": 6,
      "pay": "USD",
      "price_per_unit": 12,
      "supplier_number": 123
    }
  ]
}```
