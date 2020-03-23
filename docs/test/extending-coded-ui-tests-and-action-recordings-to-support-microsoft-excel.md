---
title: Rozšíření kódovaných testů a záznamů akcí usměrňovaného uj.
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 05ccb885c799bf2bfd2e3868b80226eca726cc31
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589549"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Rozšíření kódovaných testů a záznamů akcí v oblasti usměrňovaného rozhraní

Testovací rámec pro kódované testy uživatelského rozhraní a záznamy akcí nepodporuje všechny možné uživatelské rozhraní. Nemusí podporovat konkrétní ui, které chcete testovat. Nelze například okamžitě vytvořit kódovaný test rozhraní nebo záznam akce pro tabulku aplikace Microsoft Excel. Můžete však vytvořit vlastní rozšíření kódovaného rozhraní pro testování rozhraní, které podporuje vaše konkrétní rozhraní pomocí rozšiřitelnosti kódovaného rozhraní pro testování rozhraní.

![Architektura testu ui](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Ukázkové rozšíření pro testování aplikace Microsoft Excel

Tento [příspěvek blogu](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/3-introducing-sample-excel-extension/) obsahuje odkaz na [ukázkové rozšíření](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) pro kódované rozhraní pro testování ui. Můžete také zobrazit celou [řadu příspěvkových řad blogu pro programovou rozšiřitelnost testu ui](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/series-on-coded-ui-test-extensibility/).

> [!NOTE]
> Ukázka je určena pro použití s aplikací Microsoft Excel 2010. Může nebo nemusí fungovat s jinými verzemi aplikace Excel.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Doporučené postupy pro kódované testy rozhraní](../test/best-practices-for-coded-ui-tests.md)
- [Podporované konfigurace a platformy pro kódované testy a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
