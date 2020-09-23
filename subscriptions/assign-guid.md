---
title: Přiřazení konkrétních identifikátorů GUID předplatitelům sady Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.date: 09/21/2020
ms.topic: conceptual
description: Zjistěte, jak můžou správci určit identifikátor GUID předplatného pro předplatitele.
ms.openlocfilehash: 31544718683b10a186d4c38486bf0cd7923cd4cf
ms.sourcegitcommit: 4affcf2830337e6aba84621c3eda5faf5d0d4a01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2020
ms.locfileid: "91022475"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Přiřazení konkrétních předplatných na portálu pro správu předplatných sady Visual Studio

Správci teď můžou používat portál pro správu předplatných sady Visual Studio k přiřazení konkrétních předplatných jednotlivým předplatitelům.  To může být užitečné v situacích, kdy organizace má dočasné zaměstnance nebo dodavatele, kteří potřebují po krátkou dobu mít přístup k předplatnému.  Správci můžou přiřadit předplatné, které už je částečně používané, a nechat si nové předplatné pro delší použití.  

Podívejte se na video nebo si přečtěte, jak přiřadit určitým identifikátorům GUID k předplatným pro uživatele. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Přiřaďte uživatelům konkrétní identifikátory GUID předplatného.

Proces pro přiřazení konkrétních odběrů jednotlivcům zahrnuje využití dvou existujících procesů správy k přiřazení globálně jedinečných identifikátorů (GUID) pro konkrétní předplatné jednotlivým uživatelům.  Tento proces se skládá z exportu seznamu aktuálních předplatných a přiřazení. pomocí tohoto seznamu Identifikujte konkrétní identifikátory GUID, které chcete přiřadit, a potom pomocí procesu hromadného přidání nahrajte nová přiřazení.

### <a name="export-your-subscriptions-information"></a>Exportovat informace o předplatných

Provedení exportu:
1. Přihlaste se k [portálu pro správu](https://manage.visualstudio.com).
2. Vyberte kartu **exportovat** a soubor se stáhne do místního počítače. Tento soubor bude obsahovat název smlouvy, která obsahuje vaše uživatelská předplatná, a také datum exportu.
> [!div class="mx-imgBorder"]
> ![Exportovat předplatitele](_img/exporting-subscriptions/exporting-subscriptions.png "Kliknutím na Exportovat uložte seznam vašich přiřazených odběrů s informacemi o odběrateli.")

### <a name="identify-the-guids-you-want-to-assign"></a>Identifikujte identifikátory GUID, které chcete přiřadit.

Pokud jste dříve používali nástroj pro export, Všimněte si, že do tabulky, která je vytvořená, byla přidána nová pole.  Ty vám pomůžou určit stav každého předplatného a které chcete přiřadit uživatelům.  

- **Stav odběru**: Toto pole indikuje buď "přiřazeno" nebo "Nepřiřazeno".  Pokud má předplatné stav "přiřazeno", budou také k němu přidruženy informace o uživateli, například jméno, e-mail atd. 
- **Stav použití**: stav použití bude označovat "nové", což znamená, že nikdy nebylo přiřazeno uživateli nebo "použito", což znamená, že byl v určitém bodě přiřazen uživateli.  

Hodnoty v těchto polích spolu s dalšími informacemi v tabulce můžete použít k určení, které odběry chcete přiřadit jednotlivým uživatelům. Můžete použít filtr v aplikaci Excel, který vám umožní zúžit seznam podle stavu, úrovně předplatného, data vypršení platnosti atd. 

### <a name="upload-your-new-assignments"></a>Nahrávání nových přiřazení

Posledním krokem je stažení šablony **hromadného přidání** , vyplnění požadovaných informací pro předplatná, která chcete přiřadit, a nahrání šablony.  Úplný popis tohoto procesu najdete v článku věnovaném [Přidání více uživatelů](assign-license-bulk.md) .  

> [!IMPORTANT]
> Aby se zajistilo úspěšné nahrání, ujistěte se prosím, že:
> - Šablonu propojenou v dialogovém okně používáte při výběru **hromadného přidání**.  Nepoužívejte místně uloženou kopii šablony, protože nemusí obsahovat všechna povinná pole.  Použití staré šablony způsobí selhání nahrávání. 
> - Všechna pole zobrazená podle **požadavků** v šabloně jsou dokončená.
> - Ve sloupci **chybové zprávy** nejsou uvedené žádné chyby.
> - Každý identifikátor GUID se v šabloně používá jenom jednou. 
> - Úroveň předplatného v šabloně odpovídá předplatnému GUID v seznamu exportovaných položek. 
> - Identifikátor GUID již není přiřazen jinému uživateli v seznamu exportovaných. 

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="q-how-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>Otázka: Návody změnit, které předplatné je aktuálně přiřazeno k individuálnímu uživateli?
Odpověď: Chcete-li změnit identifikátor GUID, který je přiřazen uživateli, musíte nejprve odstranit odběr daného uživatele.  Další informace najdete v článku věnovaném [odstranění odběrů](delete-license.md) , kde najdete další informace.  Po odstranění odběru pro daného uživatele použijte postup uvedený výše k exportu seznamu a nahrání nových informací o předplatném.  

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](/visualstudio/)
- [Dokumentace ke službě Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Teď, když jste přiřadili odběry uživatelům, zjistěte, jak provádět další úlohy správy.
- [Přiřazení jednotlivých předplatných](assign-license.md)
- [Přiřazení více předplatných](assign-license-bulk.md)
- [Úprava předplatných](edit-license.md)
- [Odstranění předplatných](delete-license.md)
- [Určení maximálního využití](maximum-usage.md)


