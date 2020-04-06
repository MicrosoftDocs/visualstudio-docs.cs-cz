---
title: Poradce při potížích s balíčky VSPackages | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4827a36bd8e76462a137ae7e903c1ab624121c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698919"
---
# <a name="troubleshooting-vspackages"></a>Řešení potíží s rozšířením VSPackages
Následují běžné problémy, které můžete mít s VSPackage a tipy k vyřešení problémů.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Řešení potíží s balíčkem VSPackage, který zabraňuje spuštění sady Visual Studio

- Začněte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v nouzovém režimu.

   Chcete-li spustit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v nouzovém režimu, zadejte na příkazovém řádku **příkaz devenv.exe /safemode**.

   Během tohoto procesu žádné VSPackages jsou načteny [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]s výjimkou VSPackages, které jsou součástí .

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Chcete-li vyřešit problém v balíčku VSPackage, který se nenačte

1. Ujistěte se, že používáte kořen registru, ve kterém je registrován VSPackage ke spuštění, obvykle kořen experimentální registru.

    Další informace naleznete [v tématu Experimentální instance](../extensibility/the-experimental-instance.md).

2. Pokud je vspackage cílem spustit v kořenovém adresáři experimentálníregistru, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ujistěte se, že používáte experimentální verzi aplikace .

    Chcete-li experimentální verzi spustit, zadejte do příkazového okna **následující: devenv /rootsuffix exp**.

3. Zkontrolujte položky registru VSPackage.

    Další informace naleznete v [tématu Registrace balíčků VSPackages](registering-and-unregistering-vspackages.md) a [Správa balíčků VSPackages](../extensibility/managing-vspackages.md).

4. Otevřete **okno Výstup** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instance, která se nedaří načíst VSPackage. Informace o tom, proč VSPackage se nedaří načíst může být zobrazeny v tomto okně.

   > [!NOTE]
   > Pokud spouštíte experimentální [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z integrovaného vývojového prostředí (IDE), zkontrolujte **okno Výstup** obou verzí.

5. Zkontrolujte protokol aktivit.

    Další informace naleznete v [tématu How to: Use the Activity Log](../extensibility/how-to-use-the-activity-log.md).

6. Další informace o výjimkách vyvolaná ide, klepněte na **výjimky** v nabídce **ladění** povolit výjimky. V dialogovém okně **Výjimky** vyberte typy výjimek, o kterých chcete získat další informace.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Řešení potíží s balíčkem VSPackage, který se neregistruje

1. Ujistěte se, že sestavení VSPackage je umístěno v důvěryhodném umístění. RegPkg nemůže registrovat sestavení v nedůvěryhodném nebo částečně důvěryhodném umístění, například ve sdílené síťové složce ve výchozí konfiguraci zabezpečení .net. Přestože se zobrazí upozornění vždy, když uživatel vytvoří projekt v nedůvěryhodném umístění, zaškrtávací políčko "Nezobrazovat tuto zprávu znovu" může zabránit tomu, aby se toto upozornění opakovalo.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Poradce při potížích s příkazem, který není viditelný nebo který generuje chybu po klepnutí na příkaz

1. Sloučit nové nebo změněné příkazy nabídky a příkazy již [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v integrovaném prostředí zadáním následujícího příkazu na příkazovém řádku: **devenv /rootsuffix Exp /setup**.

2. Ujistěte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se, že můžete najít UI.dll pro váš VSPackage.

   1. Najděte CLSID balíčku VSPackage v části Balíčky v registru:

        HKLM\Software\Microsoft\Visual\\Studio*\<verze>* \balíčky

   2. Ověřte, zda je cesta daná podklíčem SatelliteDll správná.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Chcete-li vyřešit problém VSPackage, který se chová neočekávaně

1. Nastavte zarážky v kódu.

     Dobrým výchozím bodem pro ladění jsou konstruktor a metoda inicializace. Můžete také nastavit zarážky v oblasti, kterou chcete vyhodnotit, například příkaz nabídky. Chcete-li povolit zarážky, je nutné spustit pod ladicím programem.

    1. V nabídce **Project** klepněte na **položku Vlastnosti**.

    2. V dialogovém okně **Stránky vlastností** vyberte kartu **Ladění.**

    3. Do pole **Argumenty příkazového řádku** zadejte kořenovou příponu vývojového prostředí, na které cílí váš VSPackage. Chcete-li například vybrat experimentální sestavení, zadejte: **/RootSuffix Exp**.

    4. V nabídce **Ladění** klikněte na **Spustit ladění** nebo stiskněte klávesu F5.

        > [!NOTE]
        > Pokud ladíte projekt, vytvořte nebo načtěte existující instanci projektu nyní.

2. Použijte protokol aktivit.

     Trace VSPackage chování zápisem informací do protokolu aktivit v klíčových bodech. Tato technika je zvláště užitečné při spuštění VSPackage v maloobchodním prostředí. Další informace naleznete v [tématu How to: Use the Activity Log](../extensibility/how-to-use-the-activity-log.md).

3. Používejte veřejné symboly.

     Chcete-li zlepšit čitelnost při ladění, můžete připojit symboly k ladicímu programu.

    1. V nabídce **Nástroje/možnosti** přejděte do dialogového okna **Ladění/symboly.**

    2. Přidat toto **umístění souboru symbolu (.pdb):**

         `https://msdl.microsoft.com/download/symbols`

    3. Chcete-li zvýšit výkon, zadejte složku mezipaměti symbolů, například:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Řešení potíží s chybějícím balíčkem VSPackage nebo některou z jeho závislostí

1. Pro spravovaný kód se ujistěte, že referenční cesty jsou správné.

   1. V nabídce **Project** klepněte na **položku Vlastnosti**.

   2. V dialogovém okně **Stránky vlastností** vyberte kartu **Odkazy** a ujistěte se, že jsou všechny cesty správné. Případně můžete použít **prohlížeč objektů** k procházení odkazovaných objektů.

        Pro spravovaný kód můžete použít [Fuslogvw.exe (Assembly Binding Log Viewer)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) k zobrazení podrobností o neúspěšných zatíženích sestavení.

2. Pro nespravovaný kód vyhledejte kód CLSID balíčku VSPackage v uzlu registru [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID:

    HKLM\Software\Microsoft\Visual\\Studio*\<verze>* \CLSID

   Ujistěte se, že položka InprocServer32 má správnou cestu dll VSPackage.

## <a name="see-also"></a>Viz také
- [Balíčky VSPackage](../extensibility/internals/vspackages.md)
