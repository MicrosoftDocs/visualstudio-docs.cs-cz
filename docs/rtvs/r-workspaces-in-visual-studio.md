---
title: Pracovní prostory R
description: Jak řídit, kde běží kód R pomocí pracovních prostorů v sadě Visual Studio.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 11b5086c934b433d4e28095c1d50471ea44e15a8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919296"
---
# <a name="control-where-r-code-runs-with-workspaces"></a>Ovládací prvek, kde běží kód R s pracovními prostory

Pracovní prostor v nástroje jazyka R pro Visual Studio (RTVS) umožňuje nakonfigurovat, kdy relaci jazyka R spustí, které může dojít v místních i vzdálených počítačích. Cílem je umožnit fungovat v každém systému se srovnatelné uživatelské prostředí, která vám dává možnost využívat výhod potenciálně výkonnější počítače založené na cloudu.

Otevřete **pracovní prostory** okno, použijte **nástroje R** > **Windows** > **pracovní prostory** příkaz nebo stisknutím klávesy **Ctrl**+**9**.

![Okno pracovní prostory v nástroje jazyka R pro Visual Studio (VS2017)](media/workspaces-window.png)

V tomto okně zelená značka zaškrtnutí označuje aktivního pracovního prostoru, ke kterému je vázán RTVS. Výběrem modrou šipkou se nastaví aktivního pracovního prostoru. Ikona nastavení (ozubené kolo) napravo od každého pracovního prostoru vám umožní změnit jeho název, umístění a argumenty příkazového řádku. Červený symbol X odebere ručně přidaných pracovního prostoru.

## <a name="save-and-reset-a-workspace"></a>Uložit a obnovit pracovní prostor

Ve výchozím nastavení RTVS neukládá stav pracovního prostoru po zavření a znovu otevřete projekt. Toto chování můžete změnit, až [možnosti pracovního prostoru](options-for-r-tools-in-visual-studio.md#workspace).

**Nástroje R** > **relace** > **resetování** příkazu a na panelu nástrojů tlačítko Obnovit v interaktivním okně také resetovat stav pracovního prostoru na libovolné čas. S vzdálených pracovních prostorů odstraní obnovení profilu uživatele, který je vytvořen při prvním připojení ke vzdálenému serveru, což účinně odstraní všechny soubory, které se shromáždily existuje.

## <a name="local-workspaces"></a>Místní pracovní prostory

Zobrazí se seznam místních pracovních prostorech všechny překladače r. nainstalované v počítači. 

Při spuštění sady Visual Studio se pokusí automaticky zjistit všechny verze prostředí R, který jste nainstalovali projitím **HKEY_LOCAL_MACHINE\Software\R Core\\**  klíč registru. Protože tato kontrola se provádí pouze při spuštění, budete muset restartovat Visual Studio, pokud instalujete novou interpreta jazyka R.

RTVS nemusí rozpoznat interpret R, který je nainstalovaný v nestandardním způsobem (například při jednoduše kopírování souborů do složky namísto spuštění instalačního programu). V takovém případě ručně vytvořte nový místní pracovní prostor R následujícím způsobem:

1. Vyberte **přidat** tlačítka v okně pracovní prostory.
1. Zadejte název pro nový pracovní prostor.
1. Zadejte cestu ke kořenové složce R, který je ten, který obsahuje *bin* složky překladač spolu s žádné volitelné argumenty příkazového řádku předané k interpretu při RTVS spuštění systému.
1. Vyberte **Uložit** po dokončení.

![Přidává se nový pracovní prostor](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Vzdálené pracovní prostory

Vzdálené pracovní prostory umožňují připojit se do relace jazyka R ve vzdáleném počítači. (Viz [nastavení vzdálených pracovních prostorů](setting-up-remote-r-workspaces.md) postup konfigurace počítače pro tento účel.)

Visual Studio nerozpozná automaticky vzdálené pracovní prostory, proto je třeba je ručně přidat **přidat** tlačítko v okno pracovní prostory, jak je popsáno v předchozí části. V takovém případě zadejte identifikátor URI vzdáleného počítače, nikoli místní cestu.

> [!Important]
> Vzdálené pracovní prostory jsou označeny identifikátorem URI, který *musí používat protokol HTTPS* zajistit soukromí a integrity komunikaci se vzdáleným počítačem. Visual Studio se nemůže připojit ke vzdálenému počítači, který nepodporuje protokol HTTPS.

> [!Note]
> Vzdálené pracovní prostory jsou ve verzi preview. Pracujeme na lepší implementace problém synchronizace souboru pro budoucí verzi jsme Vítá vás vaše nápady a zpětnou vazbu.

## <a name="remote-workspace-logon"></a>Vzdálený pracovní prostor přihlášení

Musíte použít uživatelské jméno a heslo pro přihlášení do vzdálené pracovního prostoru.

### <a name="logon-to-windows-workspace"></a>Přihlášení do pracovního prostoru Windows

Pokud váš vzdálený počítač je nastavená na použití účtu domény, můžete použít přihlašovací doménu pro přístup k vzdálené pracovní prostor. Pokud není, pak budete muset použít `machine-name\username` formátu přihlásit pomocí účtu počítače na vzdáleném počítači.

### <a name="logon-to-linux-workspace"></a>Přihlášení k pracovnímu prostoru Linux

Pro přihlášení k použití účtu systému linux `<<unix>>\username` formátu. Například, pokud již máte účet podle názvu `ruser`, pak byste měli zadat uživatelské jméno jako `<<unix>>\ruser`.

## <a name="switch-between-workspaces"></a>Přepínání mezi pracovními prostory

RTVS je vázán na jenom jeden pracovní prostor v čase. Vázané pracovní prostor je indikován malé zelenou značku zaškrtnutí v okno pracovní prostory. Ve výchozím nastavení RTVS váže k poslední otevřít místní pracovní prostor v předchozí relaci.

Chcete-li změnit aktivního pracovního prostoru, vyberte modrý šipku vedle požadovaný pracovní prostor. Tím zobrazí výzvu k uložení relace, ukončí aktuální pracovní prostor a pak se přepne do nové.

> [!Tip]
> Zakázat ukládání příkazový řádek, vyberte **nástroje R** > **možnosti** příkazů a nastavit **zobrazit dialog potvrzením před přepnutím pracovních prostorů** možnost `No`. Zobrazit [možnosti pracovního prostoru](options-for-r-tools-in-visual-studio.md#workspace).

Pokud se pokusíte přepnout do místního pracovního prostoru, který odinstaluje, nebo na vzdálený pracovní prostor, který není k dispozici, RTVS nemusí být vázána na jakémkoliv pracovním prostoru. V důsledku toho se zobrazí chyba při zadejte kód v interaktivním okně nebo jinak spusťte kód:

![Chyba při žádný pracovní prostor je vázán na RTVS](media/workspaces-disconnected-interactive-window.png)

To pokud chcete opravit, přepněte do jiného pracovního prostoru v okno pracovní prostory. Pokud nejsou k dispozici žádné pracovní prostory, budete muset nainstalovat interpret R. Můžete také zkusit restartovat Visual Studio, pokud jste nainstalovali interpretu při spuštění sady Visual Studio.

### <a name="switch-to-a-remote-workspace"></a>Přepnout na vzdálený pracovní prostor

RTVS vyzve k zadání přihlašovacích údajů, když se poprvé připojíte k vzdálený pracovní prostor a pak ukládá do mezipaměti přihlašovací údaje (pomocí zabezpečených přihlašovacích údajů schránky Windows) pro pozdější relace. Komunikace se vzdáleným serverem se pak bezpečně provádí přes protokol HTTPS (který se vyžaduje).

V závislosti na konfiguraci serveru může se zobrazit upozornění při připojování, který čte certifikátu "certifikát zabezpečení prezentovaný vzdálenou službou R neumožňuje prokázat, že se skutečně připojujete k počítači (název)."

![Certifikát podepsaný svým držitelem varování při připojení ke vzdálené pracovní prostor](media/workspaces-remote-self-signed-certificate-warning.png)

Certifikát je RTVS předložený počítači, který se snažíte připojit k dokumentu. Tento certifikát obsahuje pole, které určuje identifikátor URI tohoto počítače. Upozornění se zobrazí, když zjistí RTVS nesoulad mezi identifikátory URI v certifikátu a identifikátor URI použitý pro připojení k počítači, označující, že zabezpečení serveru může být ohrožený.

Nicméně toto upozornění se zobrazí také pokud *certifikát podepsaný svým držitelem* byl použit pro povolení HTTPS ve vzdáleném počítači místo pomocí jedné z důvěryhodného zprostředkovatele. Další informace najdete v tématu [nastavení vzdálených pracovních prostorů](setting-up-remote-r-workspaces.md).

## <a name="directories-on-local-and-remote-computers"></a>Adresáře v místních i vzdálených počítačů

Ve výchozím nastavení, když spustíte novou interpreta jazyka R v místním pracovním prostoru, aktuální pracovní adresář nastaven *%userprofile%\Documents*. Můžete změnit adresář, kdykoliv **nástroje R** > **pracovní adresář** příkazy, nebo tím, že pravým tlačítkem myši projekt v Průzkumníku řešení sady Visual Studio a výběrem příkazů, jako jsou  **Nastavte pracovní adresář zde**.

Když se poprvé připojíte ke vzdálenému počítači, RTVS automaticky vytvoří profil uživatele na základě vašich přihlašovacích údajů, který nastaví pracovní adresář *dokumenty* složky v rámci tohoto profilu. Tato složka se použije pro všechny následné vzdálené relace, které používají stejné přihlašovací údaje.

V důsledku toho je přesné umístění, ve kterém běží váš kód se může lišit mezi místní a vzdálené pracovní prostory. Ve vašem kódu pak vždy používejte relativní cesty k datové soubory a například tak, aby váš kód je přenosný napříč pracovními prostory.

Všimněte si také, že se vzdálené pracovní prostory, všechny soubory v pracovním adresáři zůstávají v místě napříč relacemi pro stejný profil uživatele. Jak je uvedeno výše, tyto soubory můžete odstranit pomocí **nástroje R** > **relace** > **resetování** příkazu (nebo na tlačítko Obnovit v interaktivní okno) při používání vzdálené pracovního prostoru. Tento příkaz znovu odstraní profilu uživatele ze serveru, který je znovu vytvořit při opětovném připojení.

## <a name="copy-project-files-to-remote-workspaces"></a>Zkopírujte soubory projektu do vzdálených pracovních prostorů

Při práci s projekty v R v sadě Visual Studio, místního počítače vždy obsahuje nejnovější soubory projektu i v případě, že používáte vzdálený pracovní prostor. To znamená při otevření projektu ve Visual Studiu (která obvykle znamená otevření řešení obsahující tento projekt) RTVS předpokládá, že obsah projektu jsou zcela umístěny v místním počítači. Vzdálený pracovní prostor v důsledku toho je pouze dočasné hostiteli pro soubory projektu a všechny výstup z kódu. To znamená, například, že při načítání souboru pomocí `source` v interaktivním okně, musí tento soubor už být na vzdáleném počítači v cestě poskytnete, nebo musí být v aktuální pracovní adresář vzdálené interpret R (sady s `setwd()`</c2>funkce).

Soubory se zkopírují na vzdálený server následujícím způsobem:

- Pro práci se soubory vzdáleně pomocí interaktivního okna, je nutné nejprve zkopírovat je ručně tak, že pravým tlačítkem myši na tyto soubory (nebo projektu) v Průzkumníku řešení a vyberete **Source vybraných**. Pro jednotlivé soubory zkopírují se do pracovního adresáře na serveru. Při kopírování do projektu, RTVS vytvoří složku pro projekt.

- Můžete také kopírovat soubory pak výběrem v Průzkumníku řešení a pak vyberete **zdroj vybrané soubory (s)**. Tato akce je načte do interaktivního okna a provádí s nimi existuje. Pokud je relace připojení ke vzdálenému počítači, soubory se zkopírují došlo poprvé.

- Když RTVS je vázán na vzdálený pracovní prostor a stisknete **F5**vyberte **ladění** > **spustit ladění**, nebo jinak začněte spouštět kód, RTVS ve výchozím nastavení zkopíruje soubor projektu do vzdálené pracovního prostoru automaticky (viz níže pro řízení tohoto chování).

- Všechny soubory, které již existují na serveru jsou přepsány.

> [!Note]
> Protože RTVS nelze zachytit spolehlivě všechna volání funkcí jazyka R, volání funkcí, jako `source()` nebo `runApp()` (pro Shiny aplikace) v interaktivním okně nemá *není* kopírování souborů do vzdáleného pracovního prostoru.

[Vlastnosti projektu](r-projects-in-visual-studio.md#project-properties) je ovládací prvek, zda RTVS zkopíruje soubory, když projekt spustit, a přesně, které soubory se zkopírují. Chcete-li otevřít tuto stránku, vyberte **projektu** > **vlastnosti (název)** příkaz nabídky nebo klikněte pravým tlačítkem na projekt v Průzkumníku řešení a vyberte **vlastnosti**.

![Vlastnosti projektu kartu s přenosem souboru nastavení spuštění](media/workspaces-remote-file-transfer-filter-settings.png)

Tady **přenos souborů při spuštění** vlastnost určuje, zda RTVS automaticky zkopíruje soubory projektu. **Soubory k přesunu** hodnotu pak přesně které soubory se přenášejí filtry. Ve výchozím nastavení je zkopírovat pouze *. R*, *. RMD*, *.sql*, *.md*, a *.cpp* soubory. Toto chování se vyhnete neúmyslně kopírování velkých datových souborů na server se každé spuštění. 

## <a name="copy-files-from-a-remote-workspace"></a>Kopírování souborů z vzdálený pracovní prostor

Pokud svůj skript jazyka R generuje soubory na serveru, můžete zpět do klienta pomocí zkopírovat tyto soubory `rtvs::fetch_file` funkce. Tato funkce přijímá na minimum, Vzdálená cesta k souboru, který chcete zkopírovat do počítače a volitelně cílovou cestu ve vašem počítači. Pokud nezadáte cestu, soubor je zkopírován do vašeho *%userprofile%\Downloads* složky.
