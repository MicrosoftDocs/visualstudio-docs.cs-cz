---
title: Zabezpečení
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ae5db15fda1914d52be192a516d70704d2ad3cf6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061743"
---
# <a name="security-in-visual-studio"></a>Zabezpečení v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zabezpečení byste měli věnovat pozornost ve všech aspektech vývoje aplikace od návrhu až po nasazení. Začněte tím, co spustíte Visual Studio. Zobrazit [uživatelská oprávnění](../ide/user-permissions-and-visual-studio.md).

 Abyste mohli efektivně vyvíjet bezpečné aplikace, měli byste znát základní principy konceptů zabezpečení a funkce zabezpečení platforem, pro které vyvíjíte. Také je třeba porozumět bezpečným technikám kódování.

## <a name="understanding-security"></a>Princip zabezpečení
 [Zabezpečení](http://msdn.microsoft.com/library/9a9621d7-8883-4a4f-a874-65e8e09e20a6) zabezpečení přístupu kódu popisuje rozhraní .NET Framework, na základě rolí zabezpečení, zásady zabezpečení a nástroje pro zabezpečení.

 [Chránit svůj kód pomocí Top deseti zabezpečení tipy každých Developer musíte znát](http://go.microsoft.com/fwlink/?LinkId=72877) popisuje problémy, které jste měli dávejte pozor na tak, aby abyste neohrozili svá data nebo systému.

## <a name="coding-for-security"></a>Kódování pro zabezpečení
 Většina chyb kódování, které mají za následek ohrožení zabezpečení, je způsobena nesprávnými úvahami vývojářů při práci s uživatelským vstupem nebo tím, že vývojáři plně nerozumí platformě, pro kterou vyvíjejí.

 [Zabezpečené kódování zásady](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) obsahuje pokyny pro klasifikaci komponent k odstranění problémů zabezpečení.

 [Osvědčené postupy zabezpečení](http://msdn.microsoft.com/library/86acaccf-cdb4-4517-bd58-553618e3ec42) popisuje přetečení vyrovnávací paměti a úplný přehled o zabezpečení pro Microsoft Visual C++ zkontroluje funkce poskytované příznak /GS za kompilace.
