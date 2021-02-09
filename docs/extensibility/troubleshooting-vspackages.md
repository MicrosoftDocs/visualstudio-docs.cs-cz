---
title: Řešení potíží s VSPackage | Microsoft Docs
description: Přečtěte si o běžných problémech, které můžete mít s tipy pro VSPackage a řešení potíží, abyste mohli problémy vyřešit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 957488adb36c54355b4fe47577a7cd5b2407864f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893513"
---
# <a name="troubleshooting-vspackages"></a>Řešení potíží s rozšířením VSPackages
Níže jsou uvedené běžné problémy, se kterými se můžete setkat se sadou VSPackage a tipy k řešení těchto problémů.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Řešení potíží VSPackage, který brání spuštění sady Visual Studio

- Spustit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v nouzovém režimu.

   Chcete-li spustit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v nouzovém režimu, zadejte na příkazovém řádku příkaz **devenv.exe/safemode**.

   Během tohoto procesu nejsou načteny žádné VSPackage s výjimkou VSPackage, které jsou součástí systému [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Řešení potíží s VSPackage, který se nenačte

1. Ujistěte se, že používáte kořen registru, ve kterém je rozhraní VSPackage registrováno pro spuštění, obvykle pro experimentální kořen registru.

    Další informace najdete v [experimentální instanci](../extensibility/the-experimental-instance.md).

2. Pokud je rozhraní VSPackage cíleno na spuštění v kořenovém adresáři experimentálního registru, ujistěte se, že používáte experimentální verzi nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

    Chcete-li spustit experimentální verzi, zadejte následující příkaz v příkazovém okně: **devenv/rootsuffix exp**.

3. Ověřte položky registru VSPackage.

    Další informace najdete v tématu [Registrace VSPackage](registering-and-unregistering-vspackages.md) a [Správa VSPackage](../extensibility/managing-vspackages.md).

4. Otevřete okno **výstup** instance [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , které selhalo při načítání VSPackage. Informace o tom, proč se rozhraní VSPackage nedaří načíst, může být zobrazeno v tomto okně.

   > [!NOTE]
   > Pokud začínáte experimentální verzi z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí (IDE), zkontrolujte okno **výstup** obou verzí.

5. Projděte si protokol aktivit.

    Další informace najdete v tématu [Postupy: použití protokolu aktivit](../extensibility/how-to-use-the-activity-log.md).

6. Další informace o výjimkách vyvolaných rozhraním IDE získáte tak, že kliknete na **výjimky** v nabídce **ladění** a povolíte výjimky. V dialogovém okně **výjimky** vyberte typy výjimek, o kterých chcete získat další informace.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Řešení potíží s VSPackage, který se neregistruje

1. Ujistěte se, že se sestavení VSPackage nachází v důvěryhodném umístění. RegPkg nemůže registrovat sestavení v nedůvěryhodném nebo částečně důvěryhodném umístění, například v síťové sdílené složce ve výchozí konfiguraci zabezpečení .NET. I když se zobrazí upozornění pokaždé, když uživatel vytvoří projekt v nedůvěryhodném umístění, zaškrtávací políčko znovu nezobrazovat tuto zprávu může zabránit opětovnému výskytu tohoto upozornění.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Řešení potíží s příkazem, který není viditelný nebo který při kliknutí na příkaz vygeneruje chybu

1. Sloučením příkazů nabídky nový nebo změněno a těch, které jsou již v integrovaném vývojovém prostředí, zadáte následující příkaz na příkazovém [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] řádku: **devenv/rootsuffix exp/Setup**.

2. Ujistěte se, že [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] najdete UI.dll pro VSPackage.

   1. Vyhledejte CLSID sady VSPackage v oddílu Packages v registru:

        HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \Packages

   2. Ověřte, zda je cesta daného podklíče SatelliteDll správná.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Řešení potíží s VSPackage, který se chová neočekávaně

1. Nastavte zarážky v kódu.

     Dobrým počátečním bodem pro ladění jsou konstruktor a inicializační metoda. Můžete také nastavit zarážky v oblasti, kterou chcete vyhodnotit, jako je například příkaz nabídky. Chcete-li povolit zarážky, je nutné spustit v ladicím programu.

    1. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

    2. V dialogovém okně **stránky vlastností** vyberte kartu **ladění** .

    3. V poli **argumenty příkazového řádku** zadejte kořenovou příponu vývojového prostředí, které vaše rozhraní VSPackage cílí. Chcete-li například vybrat experimentální sestavení, zadejte: **/rootsuffix exp**.

    4. V nabídce **ladění** klikněte na příkaz **Spustit ladění** nebo stiskněte klávesu F5.

        > [!NOTE]
        > Pokud ladíte projekt, vytvořte nebo Načtěte existující instanci projektu nyní.

2. Použijte protokol aktivit.

     Sledujte chování VSPackage zápisem informací do protokolu aktivit v klíčových bodech. Tato technika je užitečná hlavně při spuštění sady VSPackage v maloobchodním prostředí. Další informace najdete v tématu [Postupy: použití protokolu aktivit](../extensibility/how-to-use-the-activity-log.md).

3. Používejte veřejné symboly.

     Pro zlepšení čitelnosti při ladění můžete k ladicímu programu připojit symboly.

    1. V nabídce **Nástroje/možnosti** přejděte do dialogového okna **ladění/symboly** .

    2. Přidat toto **umístění souboru se symboly (. pdb)**:

         `https://msdl.microsoft.com/download/symbols`

    3. Chcete-li zvýšit výkon, zadejte složku mezipaměti symbolů, například:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Řešení potíží s chybějícím VSPackage nebo některou z jeho závislostí

1. Pro spravovaný kód zkontrolujte, zda jsou cesty odkazů správné.

   1. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

   2. V dialogovém okně **stránky vlastností** vyberte kartu **odkazy** a ujistěte se, že jsou všechny cesty správné. Alternativně můžete použít **Prohlížeč objektů** k procházení odkazovaných objektů.

        Pro spravovaný kód můžete použít [Fuslogvw.exe (Assembly Binding Log Viewer)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) k zobrazení podrobností o neúspěšném načtení sestavení.

2. Pro nespravovaný kód vyhledejte identifikátor CLSID rozhraní VSPackage v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uzlu registru CLSID:

    HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \CLSID

   Ujistěte se, že položka InprocServer32 má správnou cestu k knihovně VSPackage dll.

## <a name="see-also"></a>Viz také
- [Balíčky VSPackage](../extensibility/internals/vspackages.md)
- [Řešení potíží s Visual Studiem](/troubleshoot/visualstudio/welcome-visual-studio/)
