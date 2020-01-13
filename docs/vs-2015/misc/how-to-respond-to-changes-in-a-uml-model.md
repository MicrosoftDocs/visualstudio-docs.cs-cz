---
title: 'Postupy: reakce na změny v modelu UML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf88661f9ec15e1a3a25e7eb6a40bbd82335a7f4
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918722"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Postupy: Reakce na změny v modelu UML
Je možné napsat kód, který se spustí pokaždé, když dojde ke změně v modelu UML v aplikaci Visual Studio. Bude reagovat rovnoměrně na změny provedené přímo uživatelem a dalších rozšířeních sady Visual Studio. Chcete-li zjistit, které verze aplikace Visual Studio podporují modely UML, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!WARNING]
> Tyto techniky nejsou podporovány rozhraním API UML. Nemusí fungovat v budoucích verzích sady Visual Studio.

## <a name="see-also"></a>Viz také
 [Navigace](../modeling/navigate-the-uml-model.md) mezi [obslužnými rutinami událostí modelu UML rozšíření změn mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md)
 