---
title: Jak se přiřazují předplatná sady Visual Studio?
description: Předplatná můžete přiřazovat postupně jednotlivým koncovým uživatelům, případně můžete pomocí funkce Hromadné přidání rychle a snadno nahrát...
ms.faqid: group1_3
ms.topic: include
ms.assetid: 59eb35fd-ec94-41ce-b24c-a8a120976bac
author: CaityBuschlen
ms.author: cabuschl
ms.date: 12/03/2020
ms.openlocfilehash: 5a12d59f90ee2a09002efcb99c78cfd563060006
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2020
ms.locfileid: "96584572"
---
## <a name="how-do-i-assign-visual-studio-subscriptions"></a>Jak se přiřazují předplatná sady Visual Studio?

Předplatná můžete přiřazovat postupně jednotlivým koncovým uživatelům, případně můžete pomocí funkce Hromadné přidání rychle a snadno nahrát velký počet předplatitelů najednou.

Individuální přiřazení předplatných:

1. V horní části stránky na webu [manage.visualstudio.com](https://manage.visualstudio.com) vyberte [kartu Spravovat předplatitele](https://manage.visualstudio.com/subscribers).
2. Vyberte Přidat a zadejte jméno a e-mailovou adresu uživatele, kterému chcete přiřadit předplatné.
    1. Pokud vaše organizace využívá Azure Active Directory, v poli pro jméno se budou vyhledávat lidé v aktuálním adresáři. Uživatele můžete vybrat z výsledků hledání nebo přidat ručně.
3. Pokud chcete předplatiteli po přihlášení k [portálu předplatných sady Visual Studio](https://my.visualstudio.com/) umožnit přístup ke stažení softwaru, nezapomeňte v části Nastavení stahování ponechat zapnutý přepínač Stahování.
4. Vyplňte část Předvolby komunikace, abychom věděli, v jakém jazyce máme předplatitelům odeslat e-mail o přiřazení.
5. Pokud chcete k přiřazení přidat nějaké poznámky, udělejte to v části Reference.
6. Výběrem možnosti Přidat v dolní části kontextového panelu dokončete přiřazení předplatného. Předplatitel obdrží e-mail a může okamžitě začít používat své předplatné sady Visual Studio (od předplatitele se nevyžaduje aktivace).

Hromadné přiřazení předplatných:

1. V horní části stránky na webu [manage.visualstudio.com](https://manage.visualstudio.com) vyberte [kartu Spravovat předplatitele](https://manage.visualstudio.com/subscribers).
2. Vyberte Hromadné přidání, stáhněte si šablonu aplikace Excel a uložte si její lokální kopii.
3. Vyžaduje se vyplnění všech polí s výjimkou pole Reference.
    1. Ujistěte se, že žádné z polí formuláře neobsahuje čárky.
    2. Odstraňte mezery na začátku a konci polí formuláře.
    3. Ujistěte se, že jména a příjmení skládající se z více částí neobsahují mezery mezi jednotlivými částmi (pokud má například jméno uživatele dvě části jako Petr Pavel, mělo by se zadat jako PetrPavel).
4. Vraťte se na web [manage.visualstudio.com](https://manage.visualstudio.com), vyberte Hromadné přidání a nahrajte uloženou kopii šablony aplikace Excel.
5. Po úspěšném nahrání se zobrazí stránka s potvrzením a seznam předplatitelů s vašimi novými předplatiteli. Předplatitelé obdrží e-mail a můžou okamžitě začít používat svá předplatná sady Visual Studio (od předplatitelů se nevyžaduje aktivace).

[Přečtěte si další informace](https://docs.microsoft.com/visualstudio/subscriptions/assign-license#add-a-single-subscriber) o přiřazování předplatných na portálu pro správce předplatných sady Visual Studio, kde se dozvíte více o rychlém a snadném přiřazování předplatných.  [Přečtěte si další informace](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) o správě předplatných sady Visual Studio s GitHub Enterprise. 

## <a name="what-is-the-github-enterprise-setup-process"></a>Co je proces nastavení předplatného GitHub Enterprise? 

Předplatné GitHub Enterprise se nastavuje a spravuje odděleně od předplatných sady Visual Studio. Po zakoupení předplatného sady Visual Studio s GitHub Enterprise je proces nastavení účtu GitHub Enterprise inicializován paralelně se (ale odděleně od) zřízením smlouvy na webu manage.visualstudio.com. Zřízení tohoto účtu GitHub Enterprise může nějakou dobu trvat.  

Jakmile vaše společnost nastaví účet GitHub Enterprise, obdrží předplatitelé, kteří mají přiřazené předplatné sady Visual Studio s GitHub Enterprise, e-mail z GitHubu s oznámením, že jejich předplatná sady Visual Studio byla propojena. Po přijetí tohoto e-mailu můžou předplatitelé kontaktovat správce organizace v GitHubu, aby dostali pozvánku do příslušné organizace. 

[Přečtěte si další informace](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) o správě předplatných sady Visual Studio s GitHub Enterprise. Další podrobnosti o procesu nastavení předplatného GitHub Enterprise najdete v [dokumentaci pro předplatitele](https://docs.microsoft.com/visualstudio/subscriptions/access-github). 