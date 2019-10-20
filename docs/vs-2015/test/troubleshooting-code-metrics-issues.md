---
title: Řešení potíží s metrikami kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3eda4127e046c7676525f1755f148663f58ec9b4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672079"
---
# <a name="troubleshooting-code-metrics-issues"></a>Řešení potíží s metrikami kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když shromáždíte metriky kódu, může dojít k některým z následujících problémů:

- [Změny ve výpočtech složitosti kódu sady Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

## <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Změny ve výpočtech složitosti kódu sady Visual Studio 2010

U stejné funkce se metrika složitosti kódu vypočtená v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] může lišit od metriky počítané předchozími verzemi [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] v následujících situacích:

- Funkce obsahuje jeden nebo více bloků catch. V předchozích verzích [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] nebyly do výpočtu zahrnuty bloky catch. V [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] je složitost každého bloku catch přidána ke složitosti funkce.

- Funkce obsahuje příkaz switch (Select Case in VB). Rozdíly ve kompilátorech mezi [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] a staršími verzemi mohou generovat jiný kód jazyka MSIL pro některé příkazy Switch, které obsahují případy vzpadne.

## <a name="see-also"></a>Viz také:

- [Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
