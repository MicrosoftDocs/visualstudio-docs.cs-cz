---
title: Práce s několika uživatelskými účty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b73c865c-74e0-420e-89cc-43524f4aafd0
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93f029a067e5a45930c2ac827862c1807e32aff8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176264"
---
# <a name="work-with-multiple-user-accounts"></a>Práce s několika uživatelskými účty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud máte více účtů Microsoft a/nebo pracovní nebo školní účty, můžete ho přidat vše do sady Visual Studio, takže mají přístup k prostředkům z libovolného účtu bez nutnosti přihlásit se k němu samostatně. K datu Visual Studio 2015 RTM podporu služeb Azure, služby Application Insights, Team Foundation Server a Office 365 zjednodušené přihlašování. Další služby může být k dispozici odehrává.  
  
 Po přidání více účtů na jednom počítači tuto sadu účtů zpřístupní se, pokud se přihlásíte k sadě Visual Studio na jiném počítači. Je důležité si uvědomit, že i když přesouvat názvy účtů, není to přihlašovací údaje. Proto se výzva k zadání přihlašovacích údajů pro tyto účty poprvé pokusí použít svoje prostředky na nový počítač.  
  
 Tento návod ukazuje, jak přidat více účtů sady Visual Studio a tom, jak zjistit, že prostředky dostupné z těchto účtů se projeví v umístění, jako **přidat připojenou službu** dialogového okna, **Průzkumníka serveru** , a **Team Explorer**.  
  
#### <a name="sign-in-to-visual-studio"></a>Přihlášení k sadě Visual Studio  
  
1.  Visual Studio 2015 se přihlaste pomocí účtu Microsoft nebo účtu organizace. Měli byste vidět vaše uživatelské jméno v pravém horním rohu okna, podobně jako tato:  
  
     ![Currentlly přihlášeného uživatele](../ide/media/vs2015-username.png "VS2015_UserName")  
  
### <a name="access-your-azure-account-in-server-explorer"></a>Přístup k účtu Azure v Průzkumníku serveru  
 Stisknutím klávesy **stisknutím Ctrl + Alt + S** otevřete **Průzkumníka serveru**. Klikněte na ikonu Azure a rozšiřuje vám měly zobrazit prostředky, které jsou k dispozici v účtu Azure, který je přidružený Identifikátor, který jste použili k přihlášení do sady Visual Studio 2015. S výjimkou, že se zobrazí vaše vlastní prostředky, ne pan Michal společnosti měl by vypadat nějak podobně:  
  
 ![Rozbalení uzlu nástroje Azure znázorňující Server Explorer](../ide/media/vs2015-serverexplorer.png "VS2015_ServerExplorer")  
  
 Při prvním použití sady Visual Studio na konkrétní zařízení, dialogové okno se zobrazí pouze předplatná zaregistrovaný pod ID, které jste přihlášení k prostředí IDE s. Mít přístup k prostředkům pro všechny vaše účty přímo z **Průzkumníka serveru** tak, že kliknete pravým tlačítkem na uzel Azure a zvolíte **spravovat a filtrovat předplatná** a přidání z vašich účtů ovládací prvek výběru účtu. Jiný účet, můžete pak v případě potřeby klikněte na šipku dolů vyberte ze seznamu účtů a. Po výběru účtu, můžete nastavit, které odběry pod tímto účtem, které chcete zobrazit v Průzkumníku serveru.  
  
 ![Spravovat předplatná Azure dialogu](../ide/media/vs2015-manage-subs.png "vs2015_manage_subs")  
  
 Při příštím otevření Průzkumníku serveru se zobrazí prostředky pro tento předplatná.  
  
### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Přístup k vašemu účtu Azure přes dialogové okno Přidat připojenou službu  
  
1.  Vytvoření projektu univerzální aplikace v jazyce C#.  
  
2.  Klikněte pravým tlačítkem na uzel projektu v Průzkumníku řešení a zvolte **Přidat > připojenou službu**. ID přidat připojenou službu průvodce se zobrazí a zobrazí seznam služeb v účtu Azure, která souvisí s váš účet Visual Studio. Všimněte si, že není muset přihlašovat samostatně do Azure. Však nutné se přihlásit na jiné účty při prvním pokusu o přístup k jejich prostředkům z daného počítače.  
  
    > [!WARNING]
    >  Pokud je to první vytváříte Store app v sadě Visual Studio 2015 v určitém počítači, zobrazí se výzva k aktivovat zařízení pro vývoj režimu tak, že přejdete do **nastavení &#124; . Aktualizace a zabezpečení &#124; pro vývojáře** ve vašem počítači. Další informace najdete v tématu [povolit zařízení pro vývoj](https://msdn.microsoft.com/library/windows/apps/dn706236.aspx).  
  
###  <a name="access_azure"></a> Přístup k Azure Active Directory ve webovém projektu  
 Azure AD umožňuje podporu pro koncového uživatele jednotné přihlašování ve webových aplikacích ASP.NET MVC nebo ověřování AD v rámci služeb webových rozhraní API. Ověření domény se liší od účtu ověřování jednotlivých uživatelů Uživatelé, kteří mají přístup k vaší doméně služby Active Directory můžete pomocí svých existujících účtů v Azure AD pro připojení k webovým aplikacím. Aplikace Office 365 můžete také použít ověřování domény. Tento údaj zobrazíte v akci, vytvořte webovou aplikaci (**soubor > Nový Projekt > C# > Cloud > Webová aplikace ASP.NET**). V dialogovém okně Nový projekt ASP.NET zvolte **změna ověřování**. Průvodce ověřením se zobrazí a můžete zvolit jaký typ ověřování, který má použít v aplikaci.  
  
 ![Změna ověřování dialogové okno pro technologii ASP.NET](../ide/media/vs2015-change-authentication.png "VS2015_change_authentication")  
  
 Další informace o různých druzích ověřování v technologii ASP.NET, naleznete v tématu [vytváření webových projektů ASP.NET v sadě Visual Studio 2013](http://www.asp.net/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauth) (informace o ověřování je stále relevantní pro Visual Studio 2015).  
  
### <a name="access-your-visual-studio-team-services-account"></a>Přístup k vašemu účtu Visual Studio Team Services  
 V hlavní nabídce zvolte **týmu > připojit k Team Foundation Server** zobrazíte **Team Exploreru** okna. Klikněte na **vybrat týmové projekty**a potom v seznamu v části **vyberte sady Team Foundation Server**, měli byste vidět adresu URL pro váš účet Visual Studio Team Services. Když vyberete adresa URL bude být přihlášení bez nutnosti opakovaně zadávat svoje přihlašovací údaje.  
  
## <a name="add-a-second-user-account-to-visual-studio"></a>Přidejte druhý uživatelský účet do sady Visual Studio  
 Klikněte na šipku dolů vedle své uživatelské jméno v pravém horním rohu sady Visual Studio. Potom klikněte na **nastavení účtu** položky nabídky. **Account manažera** zobrazí se dialogové okno a účet přihlášení. Klikněte na tlačítko **přidat účet** odkaz v levé dolní části dialogového okna Přidat nový účet Microsoft nebo nový pracovní nebo školní účet.  
  
 ![Nástroj pro výběr účtu Visual Studio](../ide/media/vs2015-acct-picker.png "VS2015_acct_picker")  
  
 Postupujte podle zobrazených výzev a zadejte nové přihlašovací údaje účtu. Následující obrázek znázorňuje Account manažera po přidání jeho Contoso.com pracovní účet uživatele.  
  
 ![Správce účtu](../ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")  
  
## <a name="revisit-the-add-connected-services-wizard-and-server-explorer"></a>Návštěvě Průvodce přidáním připojené služby a Průzkumník serveru  
 Teď přejděte na **Průzkumníka serveru** znovu, klikněte pravým tlačítkem na uzel Azure a zvolte **spravovat a filtrovat předplatná**. Zvolte nový účet kliknutím šipku rozevíracího seznamu vedle aktuálního účtu a zvolte předplatné, které chcete zobrazit v Průzkumníku serveru. Měli byste vidět všechny služby, které jsou přidružené k zadanému odběru. I když nejste přihlášení aktuálně pomocí druhého účtu Visual Studio IDE, jste přihlášeni k tomuto účtu služby a prostředky. Totéž platí pro **Projekt > Přidat připojenou službu** a **týmu > připojit k Team Foundation Server**.



