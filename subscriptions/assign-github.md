---
title: Visual Studio + nabídka GitHub Enterprise | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/17/2020
ms.topic: conceptual
description: Správa předplatných v nabídce sady Visual Studio + GitHub Enterprise
ms.openlocfilehash: 4206332890b8be9483a0211c4b465103b1565cd0
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "91006173"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>Správa předplatných sady Visual Studio pomocí GitHubu Enterprise
Zákazníci, kteří mají smlouvu Enterprise (EA) se společností Microsoft, mají nárok na zakoupení nové nabídky předplatných, která přináší společné předplatné sady Visual Studio a společnost GitHub. Předplatitelé sady Visual Studio mají snadný a ekonomický způsob získání GitHubu Enterprise. 

Když vaše organizace koupí předplatné sady Visual Studio s GitHubem Enterprise, zřídí se a spravuje ve dvou částech.

## <a name="manage-visual-studio-subscriptions"></a>Spravovat předplatná sady Visual Studio
Když vaše organizace zakoupí předplatné sady Visual Studio pomocí GitHubu Enterprise, je část sady Visual Studio pro odběry zřízena okamžitě a odběry jsou k dispozici pro přiřazení a správu na portálu [pro správu předplatných](https://manage.visualstudio.com) sady Visual Studio. 

Další informace o správě předplatných najdete v těchto tématech:
- [Použití portálu pro správu](using-admin-portal.md)
- [Přiřazení předplatných](assign-license.md)
- [Upravit odběry](edit-license.md)
- [Odstranit předplatná](delete-license.md)
- [Nadměrná přidělení](handle-overclaimed-license.md)

> [!Important]
> Pokud jsou předplatná sady Visual Studio s GitHubem Enterprise přiřazena pomocí Správce předplatných sady Visual Studio a nikdy se nekoupí těchto předplatných, nebudou se v rámci organizace zobrazovat na GitHub Enterprise Admins. Aby se zajistilo, že předplatná pro GitHub Enterprise jsou viditelná, při prvním přiřazení předplatných byste měli koupit, včetně **aspoň jednoho** Visual Studio Professional s GitHub enterprise nebo Visual Studio Enterprise předplatné GitHub Enterprise.  
>
> Je zodpovědností zákazníka, aby bylo zajištěno, že pro každé předplatné GitHub, kterému je přiřazeno, je k dispozici odpovídající předplatné sady Visual Studio s předplatným GitHub na portálu pro správu předplatných sady Visual Studio, které bude v souladu s licenčními požadavky pro toto předplatné.

## <a name="manage-github-enterprise-subscriptions"></a>Správa předplatných GitHub Enterprise
Po zakoupení předplatných na GitHubu Enterprise můžou partneři s zákazníky z GitHubu zákazníkům vytvořit a nakonfigurovat organizace, které budou mít přístup k GitHubu a identifikují správce.  Tito správci pak obdrží oznámení, že se nastavili jako správci.  

Vzhledem k tomu, že tento proces je složitější, může trvat několik dní od zakoupení předplatných, aby bylo možné organizace a správci plně nastavit.

GitHub je k dispozici buď jako cloudový GitHub.com, nebo na místním serveru GitHub Enterprise.  Procesy pro správu těchto dvou verzí se liší.  GitHub nabízí celou řadu témat nápovědy a příručky pro správce, které vám pomůžou se správou předplatných na GitHubu Enterprise.  Poskytli jsme odkazy na vybraná témata níže.  

### <a name="githubcom"></a>GitHub.com 
Další informace o správě GitHub.com najdete v následujících tématech [nápovědy k GitHubu](https://help.github.com/en).
+ [Úplný seznam témat nápovědy](https://help.github.com/en)
+ [Správa členství ve vaší organizaci](https://help.github.com/en/articles/managing-membership-in-your-organization)
+ [Pozvání uživatelů k připojení do vaší organizace](https://help.github.com/en/articles/inviting-users-to-join-your-organization)
  - [Odebírání uživatelů z týmů/organizací](https://help.github.com/en/articles/removing-a-member-from-your-organization)
  - [Obnoví se bývalý člen vaší organizace.](https://help.github.com/en/articles/reinstating-a-former-member-of-your-organization)
+ [Správa přístupu pomocí rolí](https://help.github.com/en/articles/managing-peoples-access-to-your-organization-with-roles)
+ [Organizování uživatelů do týmů](https://help.github.com/en/articles/organizing-members-into-teams)
+ [Správa přístupu k úložištím vaší organizace](https://help.github.com/en/articles/managing-access-to-your-organizations-repositories)

### <a name="github-enterprise-server"></a>Server GitHub Enterprise
V nápovědě k GitHubu najdete různé příručky pro správce, které vám pomůžou zodpovědět otázky a poskytovat tipy ke správě implementace podnikového serveru GitHubu ve vaší organizaci.

+ [Zobrazit všechny příručky správce](https://help.github.com/en/enterprise/2.16/admin)
+ [Správa uživatelů](https://help.github.com/en/enterprise/2.16/admin/user-management)
  - [Organizace a týmy](https://help.github.com/en/enterprise/2.16/admin/user-management/organizations-and-teams)
    - [Vytváření organizací](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-organizations)
    - [Vytváření týmů](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-teams)
    - [Přidávání lidí do týmů](https://help.github.com/en/enterprise/2.16/admin/user-management/adding-people-to-teams)
    - [Odebrání lidí z týmů a organizací](https://help.github.com/en/enterprise/2.16/admin/user-management/removing-users-from-teams-and-organizations)
  - [Zabezpečení uživatele](https://help.github.com/en/enterprise/2.16/admin/user-management/user-security)
+ [Instalace a konfigurace serveru GitHub Enterprise Server](https://help.github.com/en/enterprise/2.16/admin/installation)

## <a name="support-resources"></a>Prostředky podpory

- Odpovědi na otázky k nejrůznějším tématům GitHubu najdete v nápovědě k [GitHubu](https://help.github.com/en).
- Získejte pomoc od dalších uživatelů GitHubu ve [fóru komunity GitHubu](https://github.community/).
- Pokud potřebujete pomoc s prodejem, předplatnými, účty a fakturací za předplatná sady Visual Studio, kontaktujte [podporu předplatných](https://visualstudio.microsoft.com/subscriptions/support/)sady Visual Studio
- Máte dotaz o integrovaném vývojovém prostředí (IDE) sady Visual Studio, Azure DevOps Services nebo jiných produktech nebo službách sady Visual Studio?  Navštivte [podporu sady Visual Studio](https://visualstudio.microsoft.com/support/).
- Získejte [technickou podporu](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24) pro GitHub Enterprise.   

## <a name="see-also"></a>Viz také

- [Dokumentace k sadě Visual Studio](/visualstudio/)
- [Dokumentace ke službě Azure DevOps](/azure/devops/)
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