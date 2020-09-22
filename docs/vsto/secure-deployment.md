---
title: Zabezpečené nasazení
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c838eddea5b3118c28fb33411a8c58a19d7b4a2d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810951"
---
# <a name="secure-deployment"></a>Zabezpečené nasazení
  Při vytváření řešení pro systém Office je váš vývojový počítač automaticky aktualizován, aby bylo možné spustit kód v projektu. Pokud však nasazujete řešení, je nutné poskytnout legitimaci, na které se má založit rozhodnutí o vztahu důvěryhodnosti, podepsáním řešení pomocí certifikátu nebo pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] klíče pro výzvu vztahu důvěryhodnosti. Další informace najdete v tématu [udělení vztahu důvěryhodnosti řešením pro systém Office](../vsto/granting-trust-to-office-solutions.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Pokud v případě přizpůsobení na úrovni dokumentu nasadíte dokument do umístění v síti, musíte také přidat umístění dokumentu do seznamu důvěryhodných umístění v centru zabezpečení aplikace Office. Další informace o nastavení oprávnění k dokumentu u počítačů koncových uživatelů najdete v tématu [udělení důvěryhodnosti k dokumentům](../vsto/granting-trust-to-documents.md).

## <a name="prevent-office-solutions-from-running-code"></a>Zabránit spuštění kódu v řešeních pro Office
 Správci můžou pomocí registru zabránit spuštění všech řešení Office v počítači. Pokud je otevřeno řešení Office, které má rozšíření spravovaného kódu, Visual Studio Tools for Office modul runtime zkontroluje, zda položka s názvem `Disabled` existuje v jednom z následujících klíčů registru v počítači:

- **HKEY_CURRENT_USER \Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE \Software\Microsoft\VSTO**

  Chcete-li zabránit spuštění kódu v řešeních pro systém Office, vytvořte `Disabled` položku v jednom nebo obou těchto klíčích registru a zadejte jeden z následujících datových typů a hodnot pro `Disabled` :

- REG_SZ nebo REG_EXPAND_SZ, který je nastaven na libovolný řetězec jiný než "0" (nula).

- REG_DWORD, která je nastavena na libovolnou hodnotu jinou než 0 (nula).

  Chcete-li povolit, aby řešení Office spouštěla kód, nastavte obě `Disabled` položky na hodnotu 0 (nula) nebo odstraňte položky registru.

## <a name="see-also"></a>Viz také
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Příprava počítačů na spouštění nebo hostování řešení pro systém Office](/previous-versions/bb772092(v=vs.110))
- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)