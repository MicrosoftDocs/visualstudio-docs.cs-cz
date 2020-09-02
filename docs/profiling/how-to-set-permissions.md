---
title: Jak nastavit oprávnění | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 03f508bd2ff904898d77cd5ac07c30992da63b46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85328945"
---
# <a name="how-to-set-permissions"></a>Postupy: nastavení oprávnění

Tento článek popisuje, jak správce počítače udělí oprávnění zabezpečení potřebná k profilaci uživateli nebo skupině, která nemá v tomto počítači oprávnění správce.

Základní princip zabezpečení uvádí, že aplikace by měly běžet bez více než oprávnění, která potřebují. Tato zásada platí i pro uživatele. Pokud můžou uživatelé plně platit, když jsou přihlášeni jako členové skupiny uživatelů místo skupiny správců, neměli by jim být udělená oprávnění správce. První postup: vytvoření uživatelského účtu, který má oprávnění uživatele, popisuje, jak vytvořit uživatelský účet pro člena skupiny Users.

Členové skupiny Uživatelé budou potřebovat přístup ke složkám a souborům na disku, které jsou sdíleny s ostatními členy týmu. Druhý postup, "udělení přístupu ke sdíleným souborům projektu", popisuje, jak tento přístup udělit.

Členové skupiny Uživatelé mohou spustit nástroje pro profilaci, pokud správce udělí přístup k ovladači softwaru pro nástroje pro profilaci. Poslední postup, "udělení přístupu k ovladači profilování", popisuje, jak udělit přístup k tomuto ovladači.

> [!NOTE]
> K provedení kroků v těchto postupech potřebujete oprávnění správce.

## <a name="to-create-a-user-account-that-has-user-permissions"></a>Vytvoření uživatelského účtu, který má oprávnění uživatele

1. Pravým tlačítkem myši klikněte na položku **Tento počítač** a poté klikněte na možnost **Spravovat**.

     Otevře se okno **Správa počítače** .

2. Rozbalte položku **místní uživatelé a skupiny**.

3. Klikněte pravým tlačítkem na složku **Uživatelé** a pak klikněte na **Nový uživatel**.

     Zobrazí se dialogové okno **Nový uživatel** .

4. Vyplňte pole v tomto dialogovém okně informacemi pro uživatelský účet, který vytváříte. Zadejte heslo. Volitelně můžete zaškrtnout políčko, které vyžaduje, aby uživatel při příštím přihlášení změnil heslo.

5. Klikněte na **vytvořit** a potom na **Zavřít**.

     Nový uživatel se zobrazí ve skupině Uživatelé, skupina uživatelů, kteří nemají oprávnění správce.

## <a name="to-grant-access-to-shared-project-files"></a>Chcete-li udělit přístup ke sdíleným souborům projektu

1. V Průzkumníku Windows (nebo Průzkumníku souborů) vyhledejte kořen stromu složky pro soubory projektu, které používá tento uživatel a sdílí projektový tým.

     Cesta k této složce se může podobat následujícímu:

    ```cmd
    D:\ourProject
    ```

2. Klikněte pravým tlačítkem na složku a pak klikněte na **vlastnosti**.

     Zobrazí se dialogové okno ** \<folder name> vlastnosti** .

3. Klikněte na kartu **Zabezpečení**.

4. Klikněte na název účtu uživatele v poli **název skupiny nebo jméno uživatele** .

5. Zaškrtněte políčko pro **Úplné řízení**v poli **oprávnění pro \<user name> ** .

6. Klikněte na **OK**.

     Tato možnost uděluje uživateli oprávnění ke stromu sdílené složky, který začíná složkou vybranou v kroku 5.

## <a name="to-grant-access-to-the-profiling-driver"></a>Udělení přístupu k ovladači profilace

1. Otevřete příkazový řádek jako správce.

2. Změňte adresář na:

    ```cmd
    <drive>:\Program Files\Microsoft Visual Studio 14\Team Tools\Performance Tools
    ```

3. Spusťte následující příkaz:

    ```cmd
    vsperfcmd /admin:driver,start /admin:service,start
    ```

     Tento příkaz nainstaluje a spustí ovladač pro nástroje pro profilaci.

     Tento příkaz spustí ovladač a službu profilace, aby uživatelé bez správce mohli používat funkce profilace, které jsou k dispozici v prostoru uživatelského procesu. Pouze správce může spustit příkaz. a u uživatelů bez oprávnění správce se to nepodaří.

     Všimněte si, že účinky tohoto kroku jsou vráceny po restartování počítače, Pokud neprovedete také poslední krok v tomto postupu.

4. Spusťte příkaz, který umožní přístup k funkci profilace ovladače podle uživatele nebo skupiny, která nemá přístup správce k počítači:

    ```cmd
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     Tento příkaz udělí \<user name> účtu nebo \<group name> přístup k nástrojům pro profilaci. \<right>Možnost určuje funkce profilování, ke kterým má uživatel přístup. \<right>Možnost může být jedna nebo víc z následujících hodnot:

    - FullAccess – povolí přístup ke všem metodám profilace, včetně shromažďování údajů o výkonu ze služeb, vzorkování a profilování mezi jednotlivými relacemi.

    - SampleProfiling – povolí přístup k ukázkovým metodám profilace

    - CrossSession – povolí přístup k profilování mezi relacemi, který je vyžadován pro služby profilace.

5. Volitelné Pokud chcete zachovat výsledky některého z předchozích kroků po restartování počítače, spusťte následující příkaz:

    ```cmd
    vsperfcmd /admin:driver,autostart,on
    ```

   Určení uživatelé po přihlášení budou moci používat nástroje pro profilaci bez oprávnění správce.

## <a name="see-also"></a>Viz také

[Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md) 
 [VSPerfCmd](../profiling/vsperfcmd.md) 
 [Profilace a zabezpečení systému Windows Vista](../profiling/profiling-and-windows-vista-security.md)
