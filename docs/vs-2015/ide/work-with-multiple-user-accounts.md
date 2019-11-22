---
title: Práce s několika uživatelskými účty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: b73c865c-74e0-420e-89cc-43524f4aafd0
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2f68328fb243c00c43c8ef454f10ad94c7d004a4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296780"
---
# <a name="work-with-multiple-user-accounts"></a>Práce s několika uživatelskými účty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud máte více účtů Microsoft a/nebo pracovní nebo školní účty, můžete je přidat do sady Visual Studio, abyste měli přístup k prostředkům z libovolného účtu, aniž byste se museli přihlašovat samostatně. Od verze Visual Studio 2015 RTM, Azure, Application Insights, Team Foundation Server a služeb Office 365 podporuje prostředí s možností snadného přihlašování. Další služby mohou být k dispozici v průběhu času.

 Po přidání více účtů na jednom počítači se tato sada účtů bude pohybovat s vámi, pokud se přihlásíte k sadě Visual Studio v jiném počítači. Je důležité si uvědomit, že i když název účtu roamingu nemá, přihlašovací údaje se neshodují. Proto se při prvním pokusu o použití svých prostředků na novém počítači zobrazí výzva k zadání přihlašovacích údajů pro tyto účty.

 Tento návod ukazuje, jak přidat více účtů do sady Visual Studio a jak zjistit, že prostředky dostupné z těchto účtů se projeví na místech, jako je dialogové okno **Přidat připojenou službu** , **Průzkumník serveru**a **Team Explorer**.

#### <a name="sign-in-to-visual-studio"></a>Přihlášení k sadě Visual Studio

1. Přihlaste se k Visual Studiu 2015 pomocí účet Microsoft nebo účtu organizace. Mělo by se zobrazit vaše uživatelské jméno v pravém horním rohu okna, podobně jako v tomto příkladu:

     ![Přihlášený uživatel Currentlly](../ide/media/vs2015-username.png "VS2015_UserName")

### <a name="access-your-azure-account-in-server-explorer"></a>Přístup k účtu Azure v Průzkumník serveru
 Stisknutím **kombinace kláves CTRL + ALT + S** otevřete **Průzkumník serveru**. Klikněte na ikonu Azure a když se rozšíří, měli byste vidět prostředky dostupné v účtu Azure, který je přidružený k ID, které jste použili k přihlášení do sady Visual Studio 2015. Mělo by to vypadat nějak takto, s výjimkou toho, že vidíte vlastní prostředky, ne Mr. Guido 's:

 ![Průzkumník serveru zobrazení rozbaleného uzlu nástrojů Azure](../ide/media/vs2015-serverexplorer.png "VS2015_ServerExplorer")

 Při prvním použití sady Visual Studio na jakémkoli konkrétním zařízení bude dialog zobrazovat pouze odběry registrované pod ID, které jste přihlásili k rozhraní IDE pomocí. K prostředkům pro libovolný z vašich dalších účtů můžete přistupovat přímo z **Průzkumník serveru** tak, že kliknete pravým tlačítkem na uzel Azure a zvolíte **Spravovat a filtrovat předplatná** a přidáváte svoje účty z ovládacího prvku pro výběr účtu. Kliknutím na šipku dolů a výběrem ze seznamu účtů pak můžete vybrat jiný účet, a to v případě potřeby. Po výběru účtu můžete zvolit předplatné pod tímto účtem, který chcete zobrazit v Průzkumník serveru.

 ![Dialogové okno Správa předplatných Azure](../ide/media/vs2015-manage-subs.png "vs2015_manage_subs")

 Při příštím otevření Průzkumník serveru se zobrazí prostředky pro toto předplatné.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Přístup k účtu Azure prostřednictvím dialogu Přidat připojenou službu

1. Vytvořte v C#aplikaci projekt univerzální aplikace.

2. V Průzkumník řešení klikněte pravým tlačítkem na uzel projektu a vyberte **přidat > připojenou službu**. Zobrazí se průvodce Přidat připojenou službu a zobrazí se seznam služeb v účtu Azure, který je přidružený k vašemu přihlašovacímu ID sady Visual Studio. Všimněte si, že se nemusíte přihlašovat nezávisle na Azure. Při prvním pokusu o přístup k prostředkům z daného počítače se ale budete muset přihlásit k ostatním účtům.

    > [!WARNING]
    > Pokud aplikace pro Store v aplikaci Visual Studio 2015 v určitém počítači vytváříte poprvé, budete vyzváni k povolení zařízení pro vývoj, a to tak, že přejdete na **nastavení &#124; . Aktualizace a zabezpečení &#124; pro vývojáře** na vašem počítači. Další informace najdete v tématu [Povolení vývoje zařízení](https://msdn.microsoft.com/library/windows/apps/dn706236.aspx).

### <a name="access_azure"></a>Přístup k Azure Active Directory ve webovém projektu
 Azure AD umožňuje podporu jednotného přihlašování pro koncové uživatele ve webových aplikacích ASP.NET MVC nebo ověřování AD ve službách webového rozhraní API. Ověřování domény se liší od ověřování jednotlivých uživatelských účtů; Uživatelé, kteří mají přístup k vaší doméně služby Active Directory, můžou k připojení k vašim webovým aplikacím používat svoje stávající účty Azure AD. Aplikace Office 365 mohou také používat ověřování v doméně. Pokud to chcete vidět v akci, vytvořte webovou aplikaci (**soubor > nový projekt > C# > webové aplikace Cloud > ASP.NET**). V dialogovém okně Nový projekt ASP.NET vyberte **změnit ověřování**. Zobrazí se Průvodce ověřováním, ve kterém můžete zvolit druh ověřování pro použití ve vaší aplikaci.

 ![Dialog pro změnu ověřování pro ASP.NET](../ide/media/vs2015-change-authentication.png "VS2015_change_authentication")

 Další informace o různých typech ověřování v ASP.NET najdete v tématu [vytváření webových projektů ASP.NET v Visual Studio 2013](https://docs.microsoft.com/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauth) (informace o ověřování stále platí pro sadu Visual Studio 2015).

### <a name="access-your-visual-studio-team-services-account"></a>Přístup k účtu Visual Studio Team Services
 V hlavní nabídce vyberte možnost **Team > připojit k Team Foundation Server** a zobrazte okno **Team Explorer** . Klikněte na **Vybrat týmové projekty**a potom v poli se seznamem v části **Vybrat Team Foundation Server**by se měla zobrazit adresa URL pro váš účet Visual Studio Team Services. Když vyberete adresu URL, kterou budete přihlášeni, aniž byste museli znovu zadat svoje přihlašovací údaje.

## <a name="add-a-second-user-account-to-visual-studio"></a>Přidat druhý uživatelský účet do sady Visual Studio
 Klikněte na šipku dolů vedle uživatelského jména v pravém horním rohu sady Visual Studio. Pak klikněte na položku nabídky **Nastavení účtu** . Zobrazí se dialogové okno **správce účtů** a zobrazí se účet, ke kterému jste se přihlásili. Kliknutím na odkaz **Přidat účet** v levé dolní části dialogového okna přidejte novou účet Microsoft nebo nový pracovní nebo školní účet.

 ![Výběr účtu sady Visual Studio](../ide/media/vs2015-acct-picker.png "VS2015_acct_picker")

 Postupujte podle výzev a zadejte nové přihlašovací údaje k účtu. Následující ilustrace znázorňuje správce účtů poté, co uživatel přidá svůj pracovní účet Contoso.com.

 ![Správce účtů](../ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")

## <a name="revisit-the-add-connected-services-wizard-and-server-explorer"></a>Přečtěte si průvodce přidat připojené služby a Průzkumník serveru
 Nyní přejděte na **Průzkumník serveru** znovu, klikněte pravým tlačítkem na uzel Azure a vyberte **Spravovat a filtrovat předplatná**. Kliknutím na šipku rozevíracího seznamu vedle aktuálního účtu zvolte nový účet a pak zvolte, která předplatná chcete zobrazit v Průzkumník serveru. Měly by se zobrazit všechny služby přidružené k zadanému předplatnému. I když jste momentálně přihlášení k integrovanému vývojovému prostředí sady Visual Studio s druhým účtem, jste přihlášeni ke službám a prostředkům tohoto účtu. Totéž platí pro **projekt > přidání připojené služby** a **týmu > připojení k Team Foundation Server**.
