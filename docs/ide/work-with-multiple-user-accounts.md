---
title: Práce s několika uživatelskými účty
ms.date: 07/23/2019
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 872089158b6e4dc0b55c26ad187e3b68d0501f26
ms.sourcegitcommit: b2fc9ac7d73c847508f6ed082bed026476bb3955
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2020
ms.locfileid: "77027598"
---
# <a name="work-with-multiple-user-accounts"></a>Práce s několika uživatelskými účty

Pokud máte více účtů Microsoft a/nebo pracovní nebo školní účty, můžete je přidat do sady Visual Studio, abyste měli přístup k prostředkům z libovolného účtu, aniž byste se museli přihlašovat samostatně. Služby Azure, Application Insights, Azure DevOps a Office 365 podporují moderní možnosti přihlašování.

Po přidání více účtů na jednom počítači se tato sada účtů s vámi přechází, pokud se přihlásíte k sadě Visual Studio v jiném počítači.

> [!NOTE]
> I když se názvy účtů roamingují, přihlašovací údaje ne. Při prvním pokusu o použití prostředků na novém počítači se zobrazí výzva k zadání přihlašovacích údajů pro tyto účty.

V tomto článku se dozvíte, jak přidat více účtů do sady Visual Studio. Také se dozvíte, jak zobrazit prostředky dostupné z těchto účtů na místech, jako je dialogové okno **Přidat připojenou službu** , **Průzkumník serveru**a **Team Explorer**.

## <a name="sign-in-to-visual-studio"></a>Přihlášení k sadě Visual Studio

Přihlaste se k aplikaci Visual Studio pomocí účet Microsoft nebo účtu organizace. Mělo by se zobrazit vaše uživatelské jméno v horním rohu okna, podobně jako v tomto příkladu:

![Aktuálně přihlášený uživatel](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Přístup k účtu Azure v Průzkumník serveru

Chcete-li otevřít Průzkumník serveru, zvolte možnost **zobrazit** > **Průzkumník serveru** (nebo, pokud používáte [nastavení prostředí](../ide/environment-settings.md)"Obecné", stiskněte klávesu **CTRL**+**ALT**+**S**). Rozbalte uzel **Azure** a Všimněte si, že obsahuje prostředky dostupné v účtu Azure, který je přidružený k účtu, který jste použili k přihlášení do sady Visual Studio. Vypadá podobně jako na následujícím obrázku:

![Průzkumník serveru s rozbaleným uzlem Azure](../ide/media/work-with-multiple-user-accounts/server-explorer.png)

Při prvním použití sady Visual Studio na jakémkoli konkrétním zařízení zobrazí dialog pouze odběry registrované pod účtem, pomocí kterého jste se přihlásili. K prostředkům pro libovolný z vašich dalších účtů můžete přistupovat přímo z **Průzkumník serveru** tak, že kliknete pravým tlačítkem na uzel **Azure** , zvolíte **Spravovat a filtrovat předplatná**a pak přidáte svoje účty z ovládacího prvku pro výběr účtu. Kliknutím na šipku dolů a výběrem ze seznamu účtů pak můžete vybrat jiný účet, a to v případě potřeby. Po výběru účtu můžete přizpůsobit, která předplatná se v rámci tohoto účtu mají zobrazit v **Průzkumník serveru**.

![Dialogové okno Správa předplatných Azure](../ide/media/vs2015_manage_subs.png)

Při příštím otevření **Průzkumník serveru**se zobrazí prostředky pro toto předplatné.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Přístup k účtu Azure prostřednictvím dialogu Přidat připojenou službu

1. Otevřete existující projekt nebo vytvořte nový projekt.

1. Zvolte uzel projektu v **Průzkumník řešení**a potom klikněte pravým tlačítkem a zvolte **Přidat** > **připojená služba**.

   Zobrazí se průvodce **Přidat připojenou službu** a zobrazí se seznam služeb v účtu Azure, který je přidružený k vašemu účtu přizpůsobení sady Visual Studio. Nemusíte se přihlašovat nezávisle na Azure. Při prvním pokusu o přístup k prostředkům z jiného počítače se ale budete muset přihlásit k ostatním účtům.

### <a name="access-azure-active-directory-in-a-web-project"></a>Přístup k Azure Active Directory ve webovém projektu

Azure Active Directory (AAD) umožňuje podporu jednotného přihlašování pro koncové uživatele ve webových aplikacích ASP.NET MVC nebo ověřování AD ve službách webového rozhraní API. Ověřování domény se liší od ověřování jednotlivých uživatelských účtů. Uživatelé, kteří mají přístup k vaší doméně služby Active Directory, můžou používat své stávající účty AAD pro připojení k vašim webovým aplikacím. Aplikace Office 365 mohou také používat ověřování v doméně.

::: moniker range="vs-2017"

Chcete-li se podívat v akci, vytvořte nový projekt **ASP.NET Core webové aplikace** . V dialogovém okně **Nová webová aplikace ASP.NET Core** vyberte šablonu **Webová aplikace** a pak zvolte možnost **změnit ověřování**.

::: moniker-end

::: moniker range=">=vs-2019"

Chcete-li se podívat v akci, vytvořte nový projekt **ASP.NET Core webové aplikace** . Na stránce **vytvořit novou webovou aplikaci ASP.NET Core** zvolte šablonu **Webová aplikace** a pak zvolte možnost **změnit** v části **ověřování**.

::: moniker-end

Zobrazí se dialogové okno **změnit ověřování** , kde můžete zvolit druh ověřování, které se má použít ve vaší aplikaci.

![Dialog pro změnu ověřování pro ASP.NET](../ide/media/vs2015_change_authentication.png)

Další informace o různých druzích ověřování v ASP.NET naleznete v tématu [Create ASP.NET Web Projects in Visual Studio](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#authentication-methods).

### <a name="access-your-azure-devops-organization"></a>Přístup ke svojí organizaci Azure DevOps

V hlavní nabídce vyberte možnost **Team** > **Spravovat připojení** a otevřete okno **Team Explorer-připojit** . Vyberte **Spravovat připojení** > **připojit k projektu**. V dialogovém okně **připojit k projektu** vyberte v seznamu projekt (nebo vyberte **Přidat server TFS** a zadejte adresu URL k serveru). Když vyberete adresu URL, jste přihlášeni bez nutnosti znovu zadat přihlašovací údaje.

Další informace najdete v tématu [připojení k projektům v Team Explorer](connect-team-project.md).

## <a name="add-an-additional-account-to-visual-studio"></a>Přidat další účet do sady Visual Studio

Přidání dalšího účtu do sady Visual Studio:

1. Vyberte **soubor** > **Nastavení účtu**.

1. V části **všechny účty**vyberte **Přidat účet**.

1. Na stránce **Přihlásit se k účtu** vyberte účet nebo zvolte **použít jiný účet**. Postupujte podle výzev a zadejte nové přihlašovací údaje k účtu.

Volitelné Nyní můžete přejít na **Průzkumník serveru** a zobrazit služby Azure přidružené k účtu, který jste právě přidali. V **Průzkumník serveru**klikněte pravým tlačítkem na uzel **Azure** a vyberte **Spravovat a filtrovat předplatná**. Kliknutím na šipku rozevíracího seznamu vedle aktuálního účtu zvolte nový účet a pak zvolte, která předplatná chcete zobrazit v **Průzkumník serveru**. Měly by se zobrazit všechny služby přidružené k zadanému předplatnému. I když jste se ještě přihlásili do sady Visual Studio s druhým účtem, jste přihlášeni ke službám a prostředkům tohoto účtu. Totéž platí pro **projekt** > **Přidání připojené služby** a **týmu** > **připojení k Team Foundation Server**.

### <a name="add-an-account-using-device-code-flow"></a>Přidání účtu pomocí toku kódu zařízení

V některých případech se nemůžete běžným způsobem přihlašovat nebo přidat účet. K tomu může dojít, pokud je z nějakého důvodu blokovaný Internet Explorer nebo pokud je vaše síť za bránou firewall. Pokud chcete tento problém obejít, můžete povolit *tok kódu zařízení* a přidat účet nebo znovu ověřit váš účet. Tok kódu zařízení vám umožňuje přihlásit se pomocí jiného prohlížeče nebo na jiný počítač&mdash;fyzickým nebo virtuálním virtuálním počítači (VM).

Přihlášení pomocí toku kódu zařízení:

1. Otevřete stránku [**účty**](reference/accounts-environment-options-dialog-box.md) v nabídce **nástroje** > **Možnosti** > **prostředí**a pak **při přidávání nebo opětovném ověřování účtu vyberte Povolit tok kódu zařízení**. Kliknutím na **tlačítko OK** zavřete stránky možnosti.

1. Vyberte **soubor** > **Nastavení účtu** a otevřete stránku Správa účtů.

1. V části **všechny účty**vyberte **Přidat účet** .

   V dialogovém okně se zobrazí adresa URL a kód pro vložení do webového prohlížeče.

   ![Adresa URL a kód toku kódu zařízení](media/work-with-multiple-user-accounts/device-login-code.png)

1. Stisknutím **kombinace kláves Ctrl**+**C** zkopírujte text dialogového okna a kliknutím na **tlačítko OK** zavřete dialogové okno. Vložte zkopírovaný text do textového editoru, jako je například Poznámkový blok. To usnadňuje kopírování kódu v dalším kroku.

1. V počítači nebo webovém prohlížeči přejděte na adresu URL pro přihlášení k zařízení, které chcete použít k přihlášení do sady Visual Studio, a vložte nebo zadejte kód, který jste zkopírovali do pole, které říká **kód**.

   Název aplikace sady **Visual Studio** by měl být na stránce uveden dál.

1. V části **Visual Studio**klikněte na **pokračovat**.

   ![Device-Login-Page. png](media/work-with-multiple-user-accounts/device-login-page.png)

1. Podle pokynů zadejte přihlašovací údaje k účtu.

   Zobrazí se stránka s oznámením, že jste se přihlásili do sady Visual Studio na svém zařízení a že můžete zavřít okno prohlížeče.

   ![Přihlášení do sady Visual Studio prostřednictvím prohlížeče bylo dokončeno.](media/work-with-multiple-user-accounts/sign-in-browser-complete.png)

1. Vraťte se na stránku Správa účtů v sadě Visual Studio a zobrazí se nově přidaný účet v seznamu **všechny účty**. Klikněte na tlačítko **Zavřít**.

## <a name="see-also"></a>Viz také:

- [Přihlášení k sadě Visual Studio](signing-in-to-visual-studio.md)
- [Přihlášení k Visual Studio pro Mac](/visualstudio/mac/signing-in)
