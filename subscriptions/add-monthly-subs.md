---
title: Přidání nových měsíčních předplatných na portál pro správu předplatných | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 36f0d9f1-fe28-469f-a54c-dc46638270a8
ms.date: 03/19/2021
ms.topic: how-to
description: Naučte se nově zakoupit měsíční předplatná sady Visual Studio na portálu pro správu předplatných.
ms.openlocfilehash: 931f297a650926e4da5c13271a58091c9f00ddd3
ms.sourcegitcommit: d8d230791890cda532c263d04288dc13d2261c7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2021
ms.locfileid: "104757643"
---
# <a name="add-new-monthly-visual-studio-subscriptions-to-the-subscriptions-administration-portal"></a>Přidání nových měsíčních předplatných sady Visual Studio na portál pro správu předplatných
Při nákupu nových měsíčních předplatných sady Visual Studio pomocí předplatného Azure je možná budete muset přidat na portál pro správu předplatných, aby je uživatelé mohli přiřadit.  

## <a name="how-do-i-know-if-i-need-to-add-my-subscriptions"></a>Návody vědět, jestli je potřeba přidat moje odběry?
Postup přidání měsíčních předplatných závisí na tom, jaké typy předplatných vaší organizace už má, a jestli jste nový správce.
- Pokud jste novým správcem, zkontrolujeme, jestli máte při prvním přihlášení k portálu pro správu předplatných přístup k předplatným Azure, ke kterým máte oprávnění správce přístupu uživatele.  Pokud pro vás vyhledáme měsíční předplatná, přidáme je automaticky. 
- Pokud jste už přidali nebo nastavili měsíční odběry, zkontrolujeme každé měsíční předplatné pokaždé, když se přihlásíte. 
- Pokud už jste správce předplatných, který jste získali prostřednictvím multilicenčního programu, ale předtím jste nepřidali nebo nespravovali měsíční předplatná, budete je muset přidat pomocí níže uvedených kroků.

## <a name="how-to-add-monthly-subscriptions"></a>Postup přidání měsíčních předplatných
1. Přihlaste se na portál pro správu předplatných na <https://manage.visualstudio.com>
1. Na kartě **Spravovat předplatitele** vyberte rozevírací seznam **Přidat smlouvu** . 
1. V rozevíracím seznamu vyberte **Nová měsíční předplatná** .
   > [!div class="mx-imgBorder"]
   > ![Rozevírací seznam pro přidání nových měsíčních předplatných](_img/add-monthly-subs/add-subs-drop-down.png "Zvolte Přidat smlouvu a pak na nová měsíční předplatná.")
1. Systém vyhledá všechna předplatná Azure, ke kterým máte práva správce přístupu uživatele, a naimportuje všechna předplatná sady Visual Studio zakoupená pomocí těchto předplatných Azure.
1. Pokud nejsou k dispozici žádná předplatná Azure, na kterých máte práva správce přístupu k uživateli, nebo se nenašly opravňující odběry Azure, ale nenašly se žádné odběry sady Visual Studio, zobrazí se tato zpráva:
   > [!div class="mx-imgBorder"]
   > ![Nenašly se žádné nové měsíční předplatné.](_img/add-monthly-subs/no-subs-found.png "Chybová zpráva oznamující, že pro vás nejsou k dispozici žádná předplatná Azure nebo předplatné sady Visual Studio.")
1. Pokud se najde nové měsíční předplatné, zobrazí se potvrzovací zpráva.
   > [!div class="mx-imgBorder"]
   > ![Předplatná přidaná potvrzovací zpráva](_img/add-monthly-subs/subs-added-confirmation.png "V potvrzovací zprávě se zobrazí předplatná, která jste přidali.")

## <a name="things-to-keep-in-mind"></a>Co je potřeba mít na paměti
- Možnost přidání nových měsíčních předplatných bude k dispozici jenom při prvním nákupu.  Po přidání měsíčních předplatných zkontrolujeme nové odběry pokaždé, když se přihlásíte k portálu. 
- Při nalezení nových předplatných se mohou zobrazit informace o tom, že jsou již přiřazeny předplatitelům.  Důvodem je, že jiní správci mají přístup k předplatnému Azure a tito uživatelé už přiřadili nové předplatné sady Visual Studio uživatelům.  Teď, když jste je přidali také na portál, můžete spravovat tato předplatná. 

## <a name="support-resources"></a>Prostředky podpory
- Pokud potřebujete pomoc se správou předplatných sady Visual Studio, kontaktujte [podporu předplatných sady Visual Studio](https://aka.ms/vsadminhelp).

## <a name="next-steps"></a>Další kroky
Teď, když jste přidali předplatná, jste připraveni je přiřadit uživatelům.  Můžete to udělat několika způsoby:
- [Přiřadit odběry individuálně](assign-license.md)
- [Přiřazení předplatných více uživatelům](assign-license-bulk.md)
- [Přiřazení konkrétních předplatných konkrétním uživatelům](assign-guid.md)

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](/visualstudio/)
- [Dokumentace k Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoft 365](/microsoft-365/)