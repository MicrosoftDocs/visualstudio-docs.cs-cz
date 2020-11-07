---
title: Určení souborů k publikování (ClickOnce)
description: Naučte se, jak vyloučit soubory, označovat soubory jako datové soubory nebo předpoklady a vytvořit skupiny pro podmíněnou instalaci pro aplikaci ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dca403e2b4b7ac9b572e73db397433b1fae1b1ae
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350891"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Postupy: určení souborů, které jsou publikovány pomocí technologie ClickOnce
Při publikování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace jsou do aplikace nasazeny i všechny soubory neobsahující kód v projektu. V některých případech možná nebudete chtít ani potřebovat publikovat určité soubory nebo můžete chtít nainstalovat určité soubory na základě podmínek. Visual Studio poskytuje možnosti pro vyloučení souborů, označování souborů jako datových souborů nebo požadavků a vytváření skupin souborů pro podmíněnou instalaci.

 Soubory pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci jsou spravovány v dialogovém okně **soubory aplikace** , které jsou přístupné ze stránky **publikovat** v **Návrháři projektu**.

 Zpočátku je k dispozici jedna skupina souborů s názvem **(požadováno)**. Můžete vytvořit další skupiny souborů a přiřadit k nim soubory. Nemůžete změnit **skupinu pro stahování** souborů, které jsou nutné ke spuštění aplikace. Například soubory. exe nebo soubory aplikace označené jako datové soubory musí patřit do skupiny **(povinné)** .

 Výchozí hodnota stavu publikování souboru je označena jako **(auto)**. Například soubor. exe aplikace má ve výchozím nastavení stav publikování **include (auto)** .

 Soubory s vlastností **Akce sestavení** nastavenou na **obsah** jsou označeny jako soubory aplikace a budou označeny jako zahrnuté ve výchozím nastavení. Můžou být zahrnuté, vyloučené nebo označené jako datové soubory. Výjimky jsou následující:

- Datové soubory, například SQL Database ( *. mdf* a *. mdb* ) a soubory XML, budou ve výchozím nastavení označeny jako datové soubory.

- Odkazy na sestavení (soubory *. dll* ) jsou označeny následujícím způsobem při přidání odkazu: je-li **místní kopírování** **NEPRAVDA** , je označení standardně označeno jako požadované sestavení ( **předpoklad (auto)** ), které musí být přítomno v globální mezipaměti sestavení (GAC) před instalací aplikace. Pokud je **kopie Local** nastavená na **true** , sestavení je označeno jako sestavení aplikace ( **include (auto)** ) a zkopíruje se do složky aplikace při instalaci. Odkaz COM se zobrazí v dialogovém okně **soubory aplikace** (jako soubor *. ocx* ) pouze v případě, že je jeho vlastnost **Isolated** nastavena na **hodnotu true**. Ve výchozím nastavení bude součástí.

### <a name="to-add-files-to-the-application-files-dialog-box"></a>Přidání souborů do dialogového okna soubory aplikace

1. Vyberte datový soubor v **Průzkumník řešení**.

2. V okno Vlastnosti změňte vlastnost **Akce sestavení** na hodnotu **obsahu** .

### <a name="to-exclude-files-from-clickonce-publishing"></a>Vyloučení souborů z publikování ClickOnce

1. S projektem vybraným v **Průzkumník řešení** v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **publikovat** .

3. Kliknutím na tlačítko **soubory aplikace** otevřete dialogové okno **soubory aplikace** .

4. V dialogovém okně **soubory aplikace** vyberte soubor, který chcete vyloučit.

5. V poli **stav publikování** v rozevíracím seznamu vyberte **vyloučit** .

### <a name="to-mark-files-as-data-files"></a>Označení souborů jako datových souborů

1. S projektem vybraným v **Průzkumník řešení** v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **publikovat** .

3. Kliknutím na tlačítko **soubory aplikace** otevřete dialogové okno **soubory aplikace** .

4. V dialogovém okně **soubory aplikace** vyberte soubor, který chcete označit jako data.

5. V poli **stav publikování** vyberte v rozevíracím seznamu **datový soubor** .

### <a name="to-mark-files-as-prerequisites"></a>Označení souborů jako požadovaných součástí

1. S projektem vybraným v **Průzkumník řešení** v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **publikovat** .

3. Kliknutím na tlačítko **soubory aplikace** otevřete dialogové okno **soubory aplikace** .

4. V dialogovém okně **soubory aplikace** vyberte sestavení aplikace (soubor *. dll* ), které chcete označit jako požadavek. Všimněte si, že aplikace musí mít odkaz na sestavení aplikace, aby se zobrazila v seznamu.

5. V poli **stav publikování** v rozevíracím seznamu vyberte **požadované součásti** .

### <a name="to-add-a-new-file-group"></a>Přidání nové skupiny souborů

1. S projektem vybraným v **Průzkumník řešení** v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **publikovat** .

3. Kliknutím na tlačítko **soubory aplikace** otevřete dialogové okno **soubory aplikace** .

4. V dialogovém okně **soubory aplikace** vyberte pole **Skupina** pro soubor, který chcete zahrnout do nové skupiny.

    > [!NOTE]
    > Soubory musí mít vlastnost **Akce sestavení** nastavenou na **obsah** před tím, než se názvy souborů zobrazí v dialogovém okně **soubory aplikace** .

5. V poli **skupina pro stahování** vyberte v **\<New...>** rozevíracím seznamu.

6. V dialogovém okně **Nová skupina** zadejte název skupiny a klikněte na **OK**.

### <a name="to-add-a-file-to-a-group"></a>Přidání souboru do skupiny

1. S projektem vybraným v **Průzkumník řešení** v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **publikovat** .

3. Kliknutím na tlačítko **soubory aplikace** otevřete dialogové okno **soubory aplikace** .

4. V dialogovém okně **soubory aplikace** vyberte pole **Skupina** pro soubor, který chcete zahrnout do nové skupiny.

5. V poli **skupina pro stahování** vyberte skupinu z rozevíracího seznamu.

    > [!NOTE]
    > Nemůžete změnit **skupinu pro stahování** souborů, které jsou nutné ke spuštění aplikace.

## <a name="see-also"></a>Viz také
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)