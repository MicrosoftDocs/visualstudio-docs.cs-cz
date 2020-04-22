---
title: Přiřazení konkrétních identifikátorů GUID předplatitelům sady Visual Studio | Dokumenty společnosti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/20/2020
ms.topic: conceptual
description: Zjistěte, jak mohou správci určit guid předplatného pro předplatitele
ms.openlocfilehash: 722aaedcd6da0224311960d1587d0c2c24eec60f
ms.sourcegitcommit: a7f781d5a089e6aab6b073a07f3d4d2967af8aa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760156"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Přiřazení konkrétních předplatných na portálu pro správu předplatných sady Visual Studio

Správci teď můžou pomocí portálu pro správu předplatných sady Visual Studio přiřadit konkrétní předplatná jednotlivým odběratelům.  To může být užitečné v situacích, kdy organizace má dočasné zaměstnance nebo dodavatele, kteří potřebují přístup k předplatnému na krátkou dobu.  Správci mohou přiřadit předplatné, které již bylo částečně použito, takže jejich nová předplatná jsou delší dobu.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Přiřazení identifikátorů GUID konkrétního předplatného uživatelům

Proces přiřazování konkrétních předplatných jednotlivcům zahrnuje využití dvou existujících procesů správy k přiřazení konkrétních jedinečných identifikátorů předplatného (GUID) jednotlivým uživatelům.  Třístupňový proces zahrnuje export seznamu aktuálních předplatných a přiřazení, použití tohoto seznamu k identifikaci konkrétních identifikátorů GUID, které chcete přiřadit, a následné použití procesu hromadného přidání k nahrání nových přiřazení.

### <a name="export-your-subscriptions-information"></a>Export informací o předplatných

Provedení exportu:
1. Přihlaste se na [Portál pro správu](https://manage.visualstudio.com).
2. Vyberte kartu **Exportovat** a soubor se stáhne do místního počítače. Soubor bude obsahovat název smlouvy, která obsahuje vaše uživatelské odběry, stejně jako datum exportu.
> [!div class="mx-imgBorder"]
> ![Exportovat předplatitele](_img/exporting-subscriptions/exporting-subscriptions.png)

### <a name="identify-the-guids-you-want-to-assign"></a>Identifikujte identifikátory GUID, které chcete přiřadit

Pokud jste nástroj Export použili dříve, zjistíte, že do vytvořené tabulky byla přidána nová pole.  Ty vám pomohou určit stav každého předplatného a ty, které chcete přiřadit uživatelům.  

- **Stav předplatného**: Toto pole bude označovat buď "přiřazeno" nebo "nepřiřazené".  Pokud má předplatné stav "přiřazeno", bude k němu přidruženy také informace o uživateli, jako je jméno, e-mail atd. 
- **Stav použití**: Stav použití bude označovat buď "nový", což znamená, že nikdy nebyl přiřazen uživateli, nebo "použitý", což znamená, že byl uživateli přiřazen v určitém okamžiku.  

Hodnoty v těchto polích spolu s dalšími informacemi v tabulce můžete použít k určení, která předplatná chcete přiřadit jednotlivým uživatelům. Můžete použít filtr v aplikaci Excel, který vám pomůže zúžit seznam podle stavu, úrovně předplatného, data vypršení platnosti atd. 

### <a name="upload-your-new-assignments"></a>Nahrání nových úkolů

Posledním krokem je stažení šablony **hromadného přidání,** vyplnění požadovaných informací pro odběry, které chcete přiřadit, a nahrání šablony.  Úplný popis tohoto procesu naleznete v našem článku [Přidat více uživatelů.](assign-license-bulk.md)  

> [!IMPORTANT]
> Chcete-li zajistit úspěšné nahrání, ujistěte se, že:
> - Všechna pole zobrazená jako **Povinná** v šabloně jsou úplná.
> - Ve sloupci **Chybová zpráva** nejsou uvedeny žádné chyby.
> - Každý identifikátor GUID se v šabloně používá pouze jednou. 
> - Úroveň předplatného v šabloně odpovídá předplatnému identifikátoru GUID v exportovaném seznamu. 
> - Identifikátor GUID není již přiřazen jinému uživateli v exportovaném seznamu. 

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="qhow-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>Otázka: Jak změním, které předplatné je aktuálně přiřazeno jednotlivému uživateli?
A: Pokud chcete změnit, který identifikátor GUID je přiřazen uživateli, musíte nejprve odstranit předplatné pro tohoto uživatele.  Další informace naleznete v našem článku [Smazat odběry.](delete-license.md)  Po odstranění předplatného pro tohoto uživatele použijte výše uvedený proces k exportu seznamu a nahrání nových informací o předplatném.  

## <a name="see-also"></a>Viz také
- [Dokumentace sady Visual Studio](/visualstudio/)
- [Dokumentace k Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoftu 365](/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Teď, když jste uživatelům přiřadili předplatná, zjistěte, jak provádět další úlohy správy.
- [Přiřazení jednotlivých předplatných](assign-license.md)
- [Přiřazení více předplatných](assign-license-bulk.md)
- [Úprava předplatných](edit-license.md)
- [Odstranění předplatných](delete-license.md)
- [Určení maximálního využití](maximum-usage.md)


