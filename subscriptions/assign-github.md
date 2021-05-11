---
title: Přiřazení Visual Studio předplatných pomocí GitHub Enterprise | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/03/2021
ms.topic: conceptual
description: Správa předplatných v předplatných Visual Studio s GitHub Enterprise
ms.openlocfilehash: c174b9beb7a7a0eec6bdb65e684869bc0be7dadb
ms.sourcegitcommit: 8da735b586276c95bf566a867655e3464ab1f989
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2021
ms.locfileid: "109740660"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>Správa Visual Studio předplatných pomocí GitHub Enterprise
Zákazníci se smlouvami Enterprise (EA) s Microsoftem mají nárok na nákup nové nabídky předplatného, která spojuje Visual Studio předplatná a GitHub Enterprise. Je to snadný a ekonomický způsob, jak Visual Studio získat GitHub Enterprise. 

Když vaše organizace zakoupí Visual Studio předplatná s GitHub Enterprise, zř spravují se ve dvou částech.

## <a name="manage-visual-studio-subscriptions"></a>Správa Visual Studio předplatných
Když vaše organizace zakoupí Visual Studio předplatná s GitHub Enterprise, část předplatných Visual Studio se okamžitě zřovisí Visual Studio předplatná budou dostupná pro přiřazení a správu na portálu pro správu Visual Studio [Předplatná.](https://manage.visualstudio.com) Po přiřazení předplatného Visual Studio předplatného s GitHub Enterprise obdrží odběratel e-mail s informací, že má přístup ke svému předplatnému Visual Studio na adrese <https://my.visualstudio.com/subscriptions> .

Další informace o správě předplatných Visual Studio najdete v těchto tématech:
- [Použití portálu pro správu](using-admin-portal.md)
- [Přiřazení předplatných](assign-license.md)
- [Úprava předplatných](edit-license.md)
- [Odstranění předplatných](delete-license.md)
- [Nadměrná přidělení](handle-overclaimed-license.md)

> [!Important]
> Pokud Visual Studio předplatné s GitHub Enterprise přiřadí správci předplatného Visual Studio bez předchozího nákupu, GitHub nebude upozorněn, že chcete vytvořit GitHub Enterprise účet.  **Nákup alespoň jednoho** Visual Studio předplatné s GitHub Enterprise před přiřazením předplatných.

## <a name="moving-to-visual-studio-with-github-enterprise"></a>Přechod na Visual Studio s GitHub Enterprise
Pokud vaše organizace koupí předplatná sady Visual Studio se sadami GitHub Enterprise po standardních Visual Studio Enterprise a Visual Studio Professional předplatných, portál pro správu obsahuje funkci, která vám umožní přesunout stávající předplatitele na odpovídající Visual Studio Enterprise s GitHubem Enterprise nebo Visual Studio Professional s předplatnými v GitHubu Enterprise.  Například předplatitelé s předplatnými Visual Studio Professional se přesunou do Visual Studio Professional s předplatnými GitHub Enterprise. Na panelu přehled na levém panelu se zobrazí následující dlaždice:

   > [!div class="mx-imgBorder"]
   > ![Tlačítko přesunout](_img/assign-github/move-now.png "Kliknutím na přesunout teď můžete upgradovat předplatná na Visual Studio s předplatnými GitHub Enterprise.")

> [!IMPORTANT]
> Jak je uvedeno výše, zachová se stávající data předplatitelů, historie a ID předplatného a veškeré výhody, které jste aktivovali, nebudou kvůli tomuto přesunu přerušeny.  


Když kliknete na tlačítko **přesunout hned** , zobrazí se v něm panel s doporučeními pro přesun předplatných Enterprise nebo Professional:

   > [!div class="mx-imgBorder"]
   > ![Vyletět z panelu](_img/assign-github/fly-out.png)

Na této dlaždici si můžete prohlédnout ovlivněné předplatitele a určit, jestli je chcete oznámit, že po dokončení přesunu obdržíte e-mailové oznámení.  Tento e-mail informuje předplatitele o tom, že jejich výhody zůstanou beze změny, a doporučuje jim, aby zahájily nastavování přítomnosti na GitHubu.  

Kliknutím na tlačítko **přesunout předplatitele** budete moct   přesunout všechny doporučené předplatitele nebo vybrat jednotlivce ze seznamu.  Po potvrzení výběru bude trvat několik sekund, než se předplatné přesune na dokončeno. Pokud je to možné, budete muset provést tyto kroky pro samostatné verze Professional a Enterprise.  

## <a name="what-is-the-visual-studio-with-github-enterprise-setup-process"></a>Co je proces nastavení předplatného sady Visual Studio s předplatným GitHub Enterprise?
Předplatné GitHub Enterprise se nastavuje a spravuje odděleně od předplatných sady Visual Studio. Po předplatném sady Visual Studio s nákupem na GitHubu Enterprise se proces nastavení účtu GitHub Enterprise zahajuje paralelně s (ale nezávisle na), který stanovuje smlouvu v [Manage.VisualStudio.com](https://manage.visualstudio.com). Zřízení tohoto účtu GitHub Enterprise může nějakou dobu trvat. 

Jakmile vaše společnost nastaví účet GitHub Enterprise, obdrží předplatitelé, kteří mají přiřazené předplatné sady Visual Studio s GitHub Enterprise, e-mail z GitHubu s oznámením, že jejich předplatná sady Visual Studio byla propojena. Jakmile předplatitelé dostanou tento e-mail, mohou kontaktovat správce organizace GitHubu a přijmout pozvánku pro příslušnou organizaci.

Podrobnosti o nastavení GitHub Enterprise najdete v dokumentaci [pro předplatitele.](access-github.md)   

## <a name="manage-github-enterprise-subscriptions"></a>Správa GitHub Enterprise předplatných
Když GitHub Enterprise předplatná, GitHub spolupracuje se zákazníky, aby pomohl vytvořit a nakonfigurovat organizace, které budou mít přístup ke GitHubu a identifikují správce.  Tito správci pak dostanou oznámení, že byli nastaveni jako správci.  

Vzhledem k tomu, že je tento proces složitější, může trvat několik dní, než se organizace a správci plně nastaví předplatná.

GitHub je k dispozici jako cloudový GitHub.com nebo místní GitHub Enterprise Server.  Procesy správy těchto dvou verzí se liší.  GitHub poskytuje různá témata nápovědy a příručky pro správce, které vám pomůžou GitHub Enterprise předplatných.  Níže uvádíme odkazy na vybraná témata.  

## <a name="support-resources"></a>Zdroje informací o podpoře
- Další informace o přiřazení GitHubu najdete na [webu GitHub Docs.](https://docs.github.com/en/github/setting-up-and-managing-your-enterprise-account/managing-licenses-for-the-github-enterprise-and-visual-studio-bundle)
- Odpovědi na dotazy k široké škále témat GitHubu najdete v [nápovědě ke GitHubu.](https://help.github.com/en)
- Pomoc od jiných uživatelů GitHubu získáte na fóru [komunity GitHubu.](https://github.community/)
- Pokud chcete pomoc se správou Předplatná sady Visual Studio, obraťte [se Visual Studio podpory předplatných.](https://aka.ms/vsadminhelp)
- Máte dotaz ohledně integrovaného vývojového Visual Studio, Azure DevOps Services nebo jiných Visual Studio produktů nebo služeb?  Navštivte [Visual Studio podporu.](https://visualstudio.microsoft.com/support/)
- Získejte [technickou podporu](https://support.microsoft.com/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24) pro GitHub Enterprise.   

## <a name="see-also"></a>Viz také
- [Visual Studio dokumentace](/visualstudio/)
- [Dokumentace k Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Přečtěte si další informace o správě předplatných sady Visual Studio.
- [Přiřazení jednotlivých předplatných](assign-license.md)
- [Přiřazení více předplatných](assign-license-bulk.md)
- [Úprava předplatných](edit-license.md)
- [Odstranění předplatných](delete-license.md)
- [Určení maximálního využití](maximum-usage.md)

Další informace o správě předplatných sady Visual Studio pomocí GitHubu Enterprise najdete na [portálu pro správu předplatných](https://visualstudio.microsoft.com/subscriptions-administration/)sady Visual Studio.