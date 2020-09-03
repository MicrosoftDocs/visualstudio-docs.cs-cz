---
title: Přidání nových měsíčních předplatných sady Visual Studio na portál pro správu předplatných | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 36f0d9f1-fe28-469f-a54c-dc46638270a8
ms.date: 06/23/2020
ms.topic: how-to
description: Naučte se nově zakoupit měsíční předplatná sady Visual Studio na portálu pro správu předplatných.
ms.openlocfilehash: 778a3adbc9ca2117b0328a10d52904921bd0b80c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904695"
---
# <a name="add-new-monthly-visual-studio-subscriptions-to-the-subscriptions-administration-portal"></a>Přidání nových měsíčních předplatných sady Visual Studio na portál pro správu předplatných
Při nákupu nových měsíčních předplatných sady Visual Studio pomocí předplatného Azure je možná budete muset přidat na portál pro správu předplatných, aby je uživatelé mohli přiřadit.  

## <a name="how-do-i-know-if-i-need-to-add-my-subscriptions"></a>Návody vědět, jestli je potřeba přidat moje odběry?
Postup přidání měsíčních předplatných závisí na tom, jaké druhy předplatných vaší organizace už má, a jestli jste nový správce.
- Pokud jste novým správcem, zkontrolujeme, jestli máte při prvním přihlášení k portálu pro správu předplatných přístup k předplatným Azure, ke kterým máte oprávnění správce přístupu uživatele.  Pokud pro vás vyhledáme měsíční předplatná, přidáme je automaticky. 
- Pokud jste už přidali nebo nastavili měsíční odběry, zkontrolujeme každé měsíční předplatné pokaždé, když se přihlásíte. 
- Pokud už jste správcem předplatných získaných prostřednictvím multilicenčního programu, ale ještě jste předtím nepřidali nebo nespravovali měsíční předplatná, budete je muset přidat pomocí níže uvedených kroků.

## <a name="how-to-add-monthly-subscriptions"></a>Postup přidání měsíčních předplatných
1. Přihlaste se na portál pro správu předplatných na <https://manage.visualstudio.com>
1. Na kartě **Spravovat předplatitele** vyberte rozevírací seznam **nové smlouvy** . 
1. V rozevíracím seznamu vyberte **Nová měsíční předplatná** .
   > [!div class="mx-imgBorder"]
   > ![Rozevírací seznam pro přidání nových měsíčních předplatných](_img/add-monthly-subs/add-subs-drop-down.png)
1. Systém vyhledá všechna předplatná Azure, ke kterým máte práva správce přístupu uživatele, a naimportuje všechna předplatná sady Visual Studio zakoupená pomocí těchto předplatných Azure.
1. Pokud nejsou k dispozici žádná předplatná Azure, na kterých máte práva správce přístupu k uživateli, nebo se nenašly opravňující odběry Azure, ale nenašly se žádné odběry sady Visual Studio, zobrazí se tato zpráva:
   > [!div class="mx-imgBorder"]
   > ![Nenašly se žádné nové měsíční předplatné.](_img/add-monthly-subs/no-subs-found.png)
1. Pokud se najde nové měsíční předplatné, zobrazí se potvrzovací zpráva.
   > [!div class="mx-imgBorder"]
   > ![Předplatná přidaná potvrzovací zpráva](_img/add-monthly-subs/subs-added-confirmation.png)

## <a name="things-to-keep-in-mind"></a>Co je potřeba mít na paměti
- Možnost přidání nových měsíčních předplatných bude k dispozici jenom při prvním nákupu.  Po přidání měsíčních předplatných zkontrolujeme nové odběry pokaždé, když se přihlásíte k portálu. 
- Při nalezení nových předplatných se mohou zobrazit informace o tom, že jsou již přiřazeny předplatitelům.  Důvodem je, že jiní správci mají přístup k předplatnému Azure a tito uživatelé už přiřadili nové předplatné sady Visual Studio uživatelům.  Teď, když jste je přidali také na portál, můžete spravovat tato předplatná. 

## <a name="next-steps"></a>Další kroky
Teď, když jste přidali předplatná, jste připraveni je přiřadit uživatelům.  Můžete to udělat několika způsoby:
- [Přiřadit odběry individuálně](assign-license.md)
- [Přiřazení předplatných více uživatelům](assign-license-bulk.md)
- [Přiřazení konkrétních předplatných konkrétním uživatelům](assign-guid.md)

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace ke službě Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace k Azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoft 365](https://docs.microsoft.com/microsoft-365/)
