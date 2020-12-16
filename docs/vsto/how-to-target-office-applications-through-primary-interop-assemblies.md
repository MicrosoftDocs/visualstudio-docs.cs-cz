---
title: Cílové aplikace Office prostřednictvím primárních sestavení spolupráce
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově cílit systém Microsoft Office aplikací prostřednictvím primárních spolupracujících sestavení.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 81c2852a92124a7cf9fb6078b196982d22100be7
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528111"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Postupy: cílení aplikací Office prostřednictvím primárních sestavení spolupráce
  Při vytváření nového projektu sady Office aplikace Visual Studio automaticky přidá odkazy na systém Microsoft Office primární spolupracující sestavení (PIA), která jsou vyžadována pro sestavení projektu. Odkazy na jiné PIA je nutné přidat v následujících scénářích:

- Chcete v projektu používat funkce jiných systém Microsoft Office aplikací. Například můžete chtít použít funkce aplikace systém Microsoft Office Excel v projektu pro systém Microsoft Office Word.

- Chcete automatizovat systém Microsoft Office aplikací, které nemají vyhrazené projekty v aplikaci Visual Studio, jako je například přístup systém Microsoft Office.

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Přidání odkazu na primární definiční sestavení

1. Otevřete projekt Office a vyberte název projektu v **Průzkumník řešení**.

2. V nabídce **projekt** klikněte na příkaz **Přidat odkaz**.

3. Na kartě **rozhraní** vyberte v seznamu **název součásti** požadované PIA. Další informace o dostupných systém Microsoft Office primárních spolupracujících sestavení naleznete v tématu věnovaném [primárním sestavením vzájemné](../vsto/office-primary-interop-assemblies.md)spolupráce pro Office.

     Pokud je projekt cílen na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, vlastnost **Embed Interop Types** pro odkaz na sestavení je ve výchozím nastavení nastavena na **hodnotu true** . Pomocí tohoto nastavení vaše řešení nevyžaduje na počítačích koncových uživatelů PIA. Další informace najdete v tématu [Návrh a vytváření řešení pro Office](../vsto/designing-and-creating-office-solutions.md).

    > [!NOTE]
    > V projektech pro systém Office vždy přidejte odkazy na PIA sady Office pomocí karty **.NET** dialogového okna **Přidat odkaz** místo na kartě **com** . Další informace najdete v tématu [primární spolupracující sestavení pro Office](../vsto/office-primary-interop-assemblies.md).

4. Klikněte na **OK**.

     Název sestavení se zobrazí ve složce **odkazy** **Průzkumník řešení**.

## <a name="see-also"></a>Viz také
- [Sestavení primární spolupráce pro Office](../vsto/office-primary-interop-assemblies.md)
- [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)
- [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)
- [Postupy: instalace primárních sestavení vzájemné spolupráce pro systém Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
