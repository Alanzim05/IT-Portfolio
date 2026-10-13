# Email Inbox Troubleshooting

## Project Overview
Investigated and resolved a simulated help desk incident involving missing messages in NorthMail.

**Ticket ID:** INC9351235  
**Application:** NorthMail  
**Workstation:** NL-DSK-0308  
**Priority:** P4 Low  
**Environment:** SysDesks simulated help desk lab

## Problem Description
The requester reported that most inbox messages had disappeared overnight. The messages were not visible in Deleted Items, and important reports needed to be preserved.

## Investigation
1. Connected to the user's workstation through the remote desktop session.
2. Opened NorthMail.
3. Inspected the inbox and noticed that an Unread filter was active.
4. Determined that read messages were hidden from the current view.
5. Used View,Restore View to remove the filter.
6. Verified that the inbox displayed 8 items instead of 2.

## Resolution
Removed the incorrect inbox view filter. The additional messages became visible again. No emails were deleted, moved, or restored.

## Skills Demonstrated
- Remote desktop support
- Email application troubleshooting
- Inbox filter diagnosis
- User data preservation
