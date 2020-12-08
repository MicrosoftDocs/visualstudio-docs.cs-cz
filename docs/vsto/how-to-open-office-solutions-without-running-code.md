---
title: 'Postupy: otevření řešení pro systém Office bez spuštění kódu'
description: Zjistěte, jak lze otevřít dokument nebo sešit, který obsahuje rozšíření spravovaného kódu bez spuštění kódu sestavení.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8339f21fbf7add4335941360b73d42700ef6e635
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844917"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Postupy: otevření řešení pro systém Office bez spuštění kódu
  Systém Microsoft Office řešení vytvořené pomocí rozšíření spravovaného kódu běží i v případě, že nastavení zabezpečení v aplikaci Office koncového uživatele je nastaveno na hodnotu Vysoká. Je to proto, že zabezpečení kódu sestavení .NET je spravováno společností Microsoft .NET Framework, nikoli systém Microsoft Office.

 Existují však situace, kdy je vhodné otevřít dokument bez spuštění kódu. Například kód, který se spustí, když se otevře dokument, může změnit obsah, ale chcete aktualizovat způsob, jakým dokument vypadá před změnou kódu. Nebo můžete chtít odeslat dokument s určitými informacemi někomu jinému a nechcete, aby se kód spouštěl a mohl obsah také změnit.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Existuje několik způsobů, jak otevřít dokument nebo sešit, který obsahuje rozšíření spravovaného kódu bez spuštění kódu sestavení.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Obejití sestavení pomocí klávesy SHIFT

- Otevřete dokumenty a sešity v nabídce **soubor** , podržte klávesu **SHIFT** a zabráníte tak aplikaci Word a Excel ve vyvolávání událostí inicializace při otevírání dokumentu.

    > [!NOTE]
    > Pokud otevřete dokument nebo sešit v podokně úloh **Začínáme** , podržením **klávesy SHIFT** se kód neobejde. Také při stisknutí klávesy SHIFT nebrání vyvolání událostí po otevření dokumentu.

     Tato metoda je užitečná, pokud chcete otevřít dokument pro provádění změn bez kódu, který je spuštěný, a první změnu dokumentu.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Obejít sestavení přejmenováním nebo jeho odebráním

- Pokud máte potřebná oprávnění v počítači, kde je umístěno sestavení, můžete přejmenovat nebo odebrat sestavení, aby dokument nebo sešit nebyl nalezen. Výsledkem je chyba vyvolaná při každém otevření dokumentu Office.

     Pokud řešení používá více lidí, tato metoda zabrání spuštění řešení pro všechny. To může být užitečné v případě, že se problém nachází v kódu nebo odkazovaném serveru a že chcete zastavit všechny uživatele v jeho spuštění.

## <a name="see-also"></a>Viz také
- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Manifesty aplikací a nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
