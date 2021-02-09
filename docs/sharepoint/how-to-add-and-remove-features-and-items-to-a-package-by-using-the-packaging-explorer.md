---
title: 'Průzkumník balení: Přidání & odebrání funkcí & položek do balíčku'
titleSuffix: ''
description: Přidání a odebrání funkcí a položek do balíčku služby SharePoint pomocí Průzkumníka balíčků v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eec1468fc2e0c51d7dea7aa5f3ffa808b484ec87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923565"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Postupy: Přidání a odebrání funkcí a položek do balíčku pomocí Průzkumníka balíčků
  Chcete-li nakonfigurovat balíček pro nasazení položek a funkcí služby SharePoint, můžete použít Průzkumníka balíčků. Položky a funkce projektu služby SharePoint můžete upravit v souboru. wsp.

 Alternativně můžete pomocí návrháře balení zobrazit a změnit pořadí funkcí pro změnu pořadí aktivace. Další informace najdete v tématu [Postup: Přidání a odebrání funkcí a položek do balíčku pomocí návrháře balíčků](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

## <a name="open-the-packaging-explorer"></a>Otevřít Průzkumníka balíčků
 Pomocí následujícího postupu můžete otevřít Průzkumníka balíčků, pokud má řešení Visual Studio alespoň jeden projekt služby SharePoint. Případně se automaticky otevře Průzkumník balení při zobrazení funkce nebo návrháře balíčku. Po zavření všech návrhářů funkcí a balíčků se zavře i Průzkumník balíčků.

#### <a name="to-open-the-packaging-explorer"></a>Otevření Průzkumníka balíčků

1. Na panelu nabídek vyberte možnost **Zobrazit**  >  **Další**  >  **Průzkumníka balíčků** Windows.

     V sadě **nástrojů** se zobrazí **Průzkumník balení** .

## <a name="adding-a-feature-to-a-package"></a>Přidání funkce do balíčku
 Do balíčku můžete přidat nové a existující funkce pomocí Průzkumníka balíčků.

#### <a name="to-add-a-sharepoint-feature"></a>Přidání funkce SharePointu

1. Otevřete **Průzkumníka balíčků**, otevřete místní nabídku pro projekt a poté zvolte možnost **Přidat funkci**.

#### <a name="to-move-an-existing-sharepoint-feature"></a>Přesunutí existující funkce SharePointu

1. Otevřete **Průzkumníka balíčků** a pak proveďte jeden z následujících kroků:

    - Přetáhněte **funkci** z jednoho projektu do jiného projektu.

    - Otevřete místní nabídku pro funkci, zvolte **Vyjmout**, otevřete místní nabídku pro projekt, na který chcete funkci přesunout, a pak zvolte **Vložit**.

    > [!NOTE]
    > Tento postup použijte, pokud máte více než jeden projekt služby SharePoint ve vašem řešení.

## <a name="validate-a-feature-or-package"></a>Ověření funkce nebo balíčku
 Můžete identifikovat možné problémy v rámci funkcí a balíčků služby SharePoint pomocí ověření souborů. Upozornění a chyby se zobrazí v okně výstup a v Seznam chyb okně.

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Ověření funkce nebo balíčku služby SharePoint

1. Otevřete **Průzkumníka balíčků**.

2. Otevřete místní nabídku funkce nebo balíčku a zvolte možnost **ověřit**.

## <a name="see-also"></a>Viz také
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
