---
title: Rozšiřování programových testů uživatelského rozhraní a záznamů akcí
description: Naučte se vytvořit rozšíření programového testového testu uživatelského rozhraní pro konkrétní uživatelské rozhraní díky využití rozšiřitelnosti rozhraní programového testu uživatelského rozhraní.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 8c4a846fe9425af7dc62ef93276c0272f480b7f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949867"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Rozšiřování programových testů uživatelského rozhraní a záznamů akcí

Testovací rozhraní pro programové testy uživatelského rozhraní a záznamy akcí nepodporuje všechny možné uživatelské rozhraní. Nemusí podporovat konkrétní uživatelské rozhraní, které chcete testovat. Například nelze okamžitě vytvořit programový test uživatelského rozhraní nebo záznam akce pro tabulku aplikace Microsoft Excel. Můžete však vytvořit vlastní rozšíření pro programový test uživatelského rozhraní, které podporuje vaše konkrétní uživatelské rozhraní prostřednictvím rozšiřitelnosti rozhraní programového testu uživatelského rozhraní.

![Architektura testu uživatelského rozhraní](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Ukázkové rozšíření pro testování Microsoft Excelu

Tento [Blogový příspěvek](/archive/blogs/gautamg/3-introducing-sample-excel-extension) obsahuje odkaz na [ukázkové rozšíření](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) pro programové testovací rozhraní. Můžete také zobrazit celou [řadu příspěvků blogu pro rozšiřitelnost programového testu uživatelského rozhraní](/archive/blogs/gautamg/series-on-coded-ui-test-extensibility).

> [!NOTE]
> Ukázka je určena pro použití v aplikaci Microsoft Excel 2010. Může ale fungovat i v jiných verzích Excelu.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Osvědčené postupy pro programové testy uživatelského rozhraní](../test/best-practices-for-coded-ui-tests.md)
- [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)