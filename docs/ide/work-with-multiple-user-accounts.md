---
title: Práce s několika uživatelskými účty
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e623734cbe2aedee962e9f1b139ac1d50d473072
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348244"
---
# <a name="work-with-multiple-user-accounts"></a>Práce s několika uživatelskými účty

Pokud máte více účtů Microsoft a/nebo pracovní nebo školní účty, můžete ho přidat vše do sady Visual Studio, takže mají přístup k prostředkům z libovolného účtu bez nutnosti přihlásit se k němu samostatně. Služby Azure, služby Application Insights, Azure DevOps a Office 365 všechny podporují moderní prostředí přihlásit.

Po přidání více účtů na jednom počítači, že sadu účtů při roamingu s vámi, pokud se přihlásíte k sadě Visual Studio na jiném počítači.

> [!NOTE]
> I když se názvy účtů přesouvat, přihlašovací údaje nejsou. Budete vyzváni k zadání přihlašovacích údajů pro tyto účty poprvé pokusí použít svoje prostředky na nový počítač.

Tento článek ukazuje, jak přidat více účtů sady Visual Studio. Se také dozvíte, jak zobrazit prostředky, které jsou přístupné z těchto účtů na místech, jako **přidat připojenou službu** dialogového okna, **Průzkumníka serveru**, a **Team Exploreru**.

## <a name="sign-in-to-visual-studio"></a>Přihlášení k sadě Visual Studio

Přihlaste se do sady Visual Studio pomocí účtu Microsoft nebo účtu organizace. Měli byste vidět vaše uživatelské jméno se zobrazí v horním okraji okna, podobně jako tato:

![Aktuálně přihlášeného uživatele](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Přístup k účtu Azure v Průzkumníku serveru

Stisknutím klávesy **Ctrl**+**Alt**+**S** otevřete **Průzkumníka serveru**. Rozbalte **Azure** uzel a Všimněte si, že obsahuje prostředky, které jsou k dispozici v účtu Azure, který je spojen s účtem, který jste použili pro přihlášení k sadě Visual Studio. Vypadá podobně jako na následujícím obrázku:

![Průzkumník serveru s rozbalený uzel Azure](../ide/media/work-with-multiple-user-accounts/server-explorer.png)

Při prvním použití sady Visual Studio na konkrétní zařízení, dialogové okno se zobrazuje jenom předplatná zaregistrovaný pod účtem, který jste přihlášení. Mít přístup k prostředkům pro všechny vaše účty přímo z **Průzkumníka serveru** kliknutím pravým tlačítkem na **Azure** uzlu, zvolíte **spravovat a filtrovat předplatná**a následným přidáním vašich účtů z ovládacího prvku pro výběr účtu. Jiný účet, můžete pak v případě potřeby klikněte na šipku dolů vyberte ze seznamu účtů a. Po výběru účtu, si můžete přizpůsobit, které odběry pod tímto účtem zobrazíte v **Průzkumníka serveru**.

![Správa předplatných Azure dialogového okna](../ide/media/vs2015_manage_subs.png)

Při příštím otevření **Průzkumníka serveru**, se zobrazí prostředky pro dané předplatné.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Přístup k vašemu účtu Azure přes dialogové okno Přidat připojenou službu

1. Otevřete existující projekt nebo vytvořte nový projekt.

1. Zvolte uzel projektu v **Průzkumníka řešení**a pak klikněte pravým tlačítkem myši a zvolte možnost **přidat** > **připojenou službu**.

   **Přidat připojenou službu** průvodce se zobrazí a zobrazí seznam služeb v účtu Azure, který je spojen s vaším účtem přizpůsobení sady Visual Studio. Není nutné samostatně přihlášení k Azure. Však nutné se přihlásit na jiné účty při prvním pokusu o přístup k jejich prostředkům z různých počítačů.

### <a name="access-azure-active-directory-in-a-web-project"></a>Přístup k Azure Active Directory ve webovém projektu

Azure Active Directory (AAD) umožňuje podporu pro koncového uživatele jednotné přihlašování do webové aplikace ASP.NET MVC nebo ověřování AD v rámci služeb webových rozhraní API. Ověření domény se liší od účtu ověřování jednotlivých uživatelů. Uživatelé, kteří mají přístup k vaší doméně služby Active Directory můžete použít své stávající účty AAD pro připojení k webovým aplikacím. Aplikace Office 365 můžete také použít ověřování domény.

Tento údaj zobrazíte v akci, vytvořte webovou aplikaci (**souboru** > **nový projekt** > **jazyka C#** > **cloudu**  >  **Webové aplikace ASP.NET**). V **nový projekt ASP.NET** dialogovém okně zvolte **změna ověřování**. Průvodce ověřením se zobrazí a můžete zvolit jaký typ ověřování, který má použít v aplikaci.

![Změna ověřování dialogové okno pro ASP.NET](../ide/media/vs2015_change_authentication.png)

Další informace o různých druzích ověřování v technologii ASP.NET, naleznete v tématu [webové projekty ASP.NET vytvořit v sadě Visual Studio](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#authentication-methods).

### <a name="access-your-azure-devops-organization"></a>Přístup k vaší organizaci Azure DevOps

V hlavní nabídce zvolte **týmu** > **spravovat připojení** otevřít **Team Explorer – připojit** okna. Zvolte **spravovat připojení** > **připojit se k projektu**. V **připojit k projektu** dialogového okna, vyberte projekt v seznamu (nebo vyberte **přidat Server TFS** a zadejte adresu URL k vašemu serveru). Při výběru adresu URL jste přihlášeni bez nutnosti znovu zadat přihlašovací údaje.

Další informace najdete v tématu [připojit k projekty v Team Exploreru](connect-team-project.md).

## <a name="add-an-additional-account-to-visual-studio"></a>Přidat další účet se sadou Visual Studio

Chcete-li přidat další účet se sadou Visual Studio:

1. Zvolte **souboru** > **nastavení účtu**.

1. V části **všechny účty**, zvolte **přidat účet**.

1. Na **přihlásit ke svému účtu** stránky, vyberte účet nebo zvolte **použijte jiný účet**. Postupujte podle zobrazených výzev a zadejte nové přihlašovací údaje účtu.

(Volitelné) Teď můžete přejít na **Průzkumníka serveru** a podívejte se služby Azure spojené s účtem, který jste právě přidali. V **Průzkumníka serveru**, klikněte pravým tlačítkem na **Azure** uzlu a zvolte **spravovat a filtrovat předplatná**. Zvolte nový účet kliknutím na šipku rozevíracího seznamu vedle aktuálního účtu a klikněte na tlačítko odběry, které chcete zobrazit v **Průzkumníka serveru**. Měli byste vidět všechny služby, které jsou přidružené k zadanému odběru. I v případě, že jste se přihlásili není aktuálně do sady Visual Studio pomocí druhého účtu, jste přihlášeni k tomuto účtu služby a prostředky. Totéž platí pro **projektu** > **přidat připojenou službu** a **týmu** > **připojit k Team Foundation Server**.

### <a name="add-an-account-using-device-code-flow"></a>Přidání účtu služby pomocí toku kódu zařízení

V některých případech se nelze přihlásit nebo přidat účet způsobem regulárních. Tomu může dojít, pokud je aplikace Internet Explorer blokovaný z nějakého důvodu, nebo pokud se vaše síť za bránou firewall. Chcete-li tento problém obejít, můžete povolit *toku kódu zařízení* přidat účet nebo donutit vašeho účtu. Tok kódu při zařízení umožní se přihlásit pomocí jiného prohlížeče nebo na jiném počítači&mdash;fyzický nebo virtuální (VM).

K přihlášení pomocí toku kódu zařízení:

1. Otevřít [ **účty** ](reference/accounts-environment-options-dialog-box.md) stránky **nástroje** > **možnosti** > **prostředí**a pak vyberte **povolit zařízení tok kódu při přidávání nebo opětovné autentizace účet**. Zvolte **OK** ukončíte možnosti stránky.

1. Zvolte **souboru** > **nastavení účtu** otevřete stránku pro správu účtu.

1. Zvolte **přidat účet** pod **všechny účty**.

   Dialogové okno zobrazí adresu URL a kód vložte do webového prohlížeče.

   ![Adresa URL toku zařízení kódu a kódu](media/work-with-multiple-user-accounts/device-login-code.png)

1. Stisknutím klávesy **Ctrl**+**C** kopírovat text z dialogového okna a pak zvolte **OK** zavřete dialogové okno. Vložte text, který jste zkopírovali do textového editoru, jako je například Poznámkový blok. Díky tomu vás snadnější zkopírovat kód v dalším kroku.

1. Přejděte na adresu URL pro přihlášení zařízení na počítači nebo webový prohlížeč, kterou chcete použít k přihlášení k sadě Visual Studio a potom vložte nebo zadejte kód, který jste zkopírovali do pole **kód**.

   **Sady Visual Studio** název aplikace by se měla zobrazit další dolů na stránce.

1. V části **sady Visual Studio**, zvolte **pokračovat**.

   ![zařízení. přihlášení page.png](media/work-with-multiple-user-accounts/device-login-page.png)

1. Postupujte podle zobrazených výzev a zadejte svoje přihlašovací údaje.

   Zobrazí se stránka s upozorněním, že už jste se přihlašovali do sady Visual Studio na vašem zařízení, a že můžete zavřít okno prohlížeče.

   ![Visual Studio přihlášení prostřednictvím prohlížeče dokončení](media/work-with-multiple-user-accounts/sign-in-browser-complete.png)

1. Přejděte zpět na stránku pro správu účtu v sadě Visual Studio a zobrazí se vám nově přidaný účet uvedený v části **všechny účty**. Zvolte **Zavřít**.

## <a name="see-also"></a>Viz také:

- [Přihlášení k sadě Visual Studio](signing-in-to-visual-studio.md)
- [Přihlaste se k sadě Visual Studio pro Mac](/visualstudio/mac/signing-in)
