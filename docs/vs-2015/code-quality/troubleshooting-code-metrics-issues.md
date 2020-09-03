---
title: Řešení potíží s metrikami kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4d374a2737e2ce8892304b615bebcf99d9c60ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672458"
---
# <a name="troubleshooting-code-metrics-issues"></a>Řešení potíží s metrikami kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když shromáždíte metriky kódu, může dojít k některým z následujících problémů:

- [Změny ve výpočtech složitosti kódu sady Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

## <a name="changes-in-visual-studio-2010-code-complexity-calculations"></a><a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Změny ve výpočtech složitosti kódu sady Visual Studio 2010
 Pro stejnou funkci se metrika složitosti kódu vypočtená v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] může lišit od metriky počítané předchozími verzemi nástroje v [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] následujících situacích:

- Funkce obsahuje jeden nebo více bloků catch. V předchozích verzích systému [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] nebyly bloky catch zahrnuty do výpočtu. V systému [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] je složitost každého bloku catch přidána ke složitosti funkce.

- Funkce obsahuje příkaz switch (Select Case in VB). Rozdíly ve kompilátorech mezi [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] a staršími verzemi mohou vygenerovat jiný kód jazyka MSIL pro některé příkazy Switch, které obsahují případy vzpadne.

## <a name="see-also"></a>Viz také
 [Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
