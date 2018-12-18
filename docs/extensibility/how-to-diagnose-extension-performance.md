---
title: 'Postupy: Diagnostika výkonu rozšíření | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/08/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: douge
ms.workload:
- bertaygu
ms.openlocfilehash: d1f2942c9f5987a686226c94e9764b8ab6300050
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934922"
---
# <a name="measuring-extension-impact-in-startup"></a>Měření dopadu rozšíření v po spuštění

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Zaměřte se na výkon rozšíření v sadě Visual Studio 2017

Na základě názorů zákazníků, jedna z oblasti zaměření pro verze sady Visual Studio 2017 se stále výkonu načítání řešení a spuštění. Jako platformu týmu sady Visual Studio pracujeme na vylepšení výkonu načítání řešení a spuštění. Obecně platí naše měření navrhnout nainstalovaná rozšíření může mít také významný dopad na tyto scénáře.

Pomoc uživatelům porozumění tomuto vlivu, jsme přidali novou funkci v sadě Visual Studio, abyste upozornili uživatele, pomalé rozšíření. V některých případech sada Visual Studio zjistí novou příponu, která může zpomalit načítání řešení nebo při spuštění. Když se zjistí zpomalení, uživatelům se zobrazí oznámení v integrovaném vývojovém prostředí přejděte do dialogového okna Nový "Spravovat výkon sady Visual Studio". Toto dialogové okno můžete také vždy možný přes nabídku Nápověda k nalezení dříve detekované rozšíření.

![spravovat výkon sady Visual Studio](media/manage-performance.png)

Tento dokument, zaměřuje, což vývojářům rozšíření popisuje, jak se počítá rozšíření vliv. Tento dokument také popisuje, jak rozšíření dopad mohou být analyzovány místně. Místně analýza dopadu rozšíření určí, pokud rozšíření se může zobrazit jako výkon vliv na rozšíření.

> [!NOTE]
> Tento dokument se zaměřuje na dopadu rozšíření na zatížení při spuštění a řešení. Rozšíření také ovlivnit výkon sady Visual Studio, když způsobí uživatelského rozhraní přestane reagovat. Další informace o tomto tématu najdete v tématu [postupy: Diagnostika uživatelské rozhraní se zpozdí způsobených rozšířeními](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Jak rozšíření může mít vliv na spuštění

Jedním z nejběžnějších způsobů pro rozšíření, která mají vliv na výkon při spuštění je výběrem automaticky načíst na některé ze známých spuštění uživatelského rozhraní kontexty například NoSolutionExists nebo ShellInitialized. Aktivovat při spuštění těchto kontextech uživatelského rozhraní. Všechny balíčky, které patří `ProvideAutoLoad` atribut v jejich definice s těmito kontexty bude načten a inicializován v daném čase.

Když budeme měřit dopad rozšíření, především zaměříme na času spotřebovaného přidělenými těchto rozšíření, které vybrat automatického zatížení v kontextech výše. Měří dobu by obsahovat, ale není omezena na:

* Načítání sestavení rozšíření pro synchronní balíčky
* Doba trvání v konstruktoru třídy balíčků pro synchronní balíčky
* Doba trvání v metodě inicializace (nebo setsite –) balíčku pro synchronní balíčky
* Pro asynchronní balíčky výše uvedené operace běží na vlákně na pozadí.  V důsledku toho operace jsou vyloučeny z monitorování.
* Doba trvání jakékoli asynchronní práce během inicializace balíček naplánovány ke spuštění na hlavním vlákně
* Doba trvání obslužné rutiny událostí, konkrétně prostředí inicializován kontext aktivace nebo změnu stavu zombie prostředí
* Od Visual Studio 2017 Update 3, bude také začneme sledovat čas strávený ve volání nečinnosti před dokončením inicializace prostředí. Dlouhé operace v nečinnosti obslužné rutiny také způsobit reagovat integrovaného vývojového prostředí a přispívají k vnímaná spuštění uživatelem.

Přidali jsme řadu funkcí, které se spouští ze sady Visual Studio 2015. Tyto funkce pomůžou s odpadá nutnost k automatické načtení balíčků. Funkce také odložit potřebu balíčky k načtení do zvláštní případy. Tyto případy zahrnují příklady, kde uživatelé by určité více rozšíření nebo snížit dopad rozšíření při načítání automaticky.

Další podrobnosti o těchto funkcích najdete v následujících dokumentech:

[Podle pravidel kontexty uživatelského rozhraní](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): bohatší modul podle pravidel vybudována okolo kontexty uživatelského rozhraní umožňuje vytvářet vlastní kontexty na základě projektu typů, typů a pro atributy. Vlastní kontexty slouží k načtení balíčku během konkrétnější scénáře. Mezi tyto konkrétní scénáře patří přítomnost projekt s konkrétní možnosti namísto spuštění. Vlastní kontextů také povolit [příkaz viditelnost vlastnit vlastní místní](visibilityconstraints-element.md) podle součásti projektu nebo jiné dostupné podmínky. Tato funkce eliminuje potřebu načíst balíček pro registraci obslužná rutina příkazu stav dotazu.

[Podpora asynchronního balíčku](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): nové AsyncPackage základní třídy v sadě Visual Studio 2015 umožňuje balíčků sady Visual Studio na načtení na pozadí asynchronně Pokud balíček zatížení požadovanou automatické zatížení atribut nebo dotazu asynchronní služby . Toto načtení na pozadí umožňuje IDE, aby byla schopná reagovat. Rozhraní IDE je responzivní, dokonce i za běhu rozšíření je inicializován na pozadí a důležité scénáře, jako je spuštění a řešení zatížení nebude mít vliv.

[Asynchronní služby](how-to-provide-an-asynchronous-visual-studio-service.md): podporující asynchronní balíček, také přidali jsme podporu pro dotazování služby asynchronně a nebudou moct zaregistrovat asynchronní služby. Důležitější ale pracujeme na převod základních služeb Visual Studio pro podporu asynchronního dotazu tak, aby většina práce v dotazu asynchronní probíhá vláken na pozadí. SComponentModel (Visual Studio MEF hostitele) je jedním z hlavních služeb, které teď podporuje asynchronního dotazu umožňující rozšíření pro podporu zcela asynchronní načítání.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Snižuje dopad automaticky načíst rozšíření

Pokud balíček přesto musí být načteny při spuštění automatického, je důležité, abyste minimalizovali práci během inicializace balíčku. Minimalizuje práci inicializace balíček snižuje možnost rozšíření na vliv. Po spuštění.

Některé příklady, které by mohly způsobit balíček inicializace drahé jsou:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Použití synchronní balíček zatížení namísto zatížení asynchronní balíčku

Protože synchronní balíčky jsou načteny v hlavním vlákně ve výchozím nastavení, doporučujeme vlastníků rozšíření, které mají balíčky automaticky načíst místo toho, jak bylo zmíněno dříve použít základní třídy asynchronní balíčku. Změna k automaticky načíst balíček pro podporu asynchronní načítání se také usnadňují vyřešit následující problémy.

### <a name="synchronous-filenetwork-io-requests"></a>Požadavků na vstupně-výstupních operací synchronní souboru/sítě

V ideálním případě mělo by se vyhnout jakékoli synchronní vstupně-výstupní operace požadavku souboru nebo sítě v hlavním vlákně. Jejich dopad bude záviset na stav počítače a můžete zablokovat pro dlouhou dobu v některých případech.

Pomocí balíčku asynchronní načítání a asynchronní vstupně-výstupní operace rozhraní API by měl Ujistěte se, že tento balíček inicializace nebrání v hlavní vlákno v takových případech. Uživatelé také mohou nadále pracovat se sadou Visual Studio během vstupně-výstupních požadavků dochází v pozadí.

### <a name="early-initialization-of-services-components"></a>Časná inicializace služby komponent

Jednou z běžných vzorech v balíčku inicializace je inicializace služby používané nebo poskytované tento balíček v balíčku `constructor` nebo `initialize` metody. Přestože tím se zajistí, že služby jsou připravená k použití, můžete také přidat zbytečné náklady pro balíček načítání, pokud tyto služby nejsou okamžitě použity. Místo toho je třeba inicializovat tyto služby na vyžádání, abyste minimalizovali práci v balíčku inicializace.

Pro zadaný balíček služeb global services, můžete použít `AddService` metody, které přebírají funkci laxně inicializovat službu pouze v případě, že je požadovaná komponenta. Pro služby používané v rámci balíčku, můžete použít opožděné<T> nebo AsyncLazy<T> abyste měli jistotu, že služby jsou inicializována nebo dotazovat při prvním použití.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Měření dopadu automaticky načíst rozšíření pomocí protokolu aktivit

Od Visual Studio 2017 Update 3, protokol aktivit v sadě Visual Studio nyní obsahovala položky dopad na výkon balíčků při načítání řešení a spuštění. Chcete-li zobrazit tyto rozměry, budete muset spustit aplikaci Visual Studio s přepínačem/log a otevřete *ActivityLog.xml* souboru.

V protokolu aktivit položky bude v části "Spravovat výkon sady Visual Studio" zdroj a bude vypadat jako v následujícím příkladu:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Tento příklad ukazuje, že balíček s identifikátorem GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" strávený 2008 ms v po spuštění sady Visual Studio. Všimněte si, že Visual Studio bere v úvahu náklady na nejvyšší úrovni jako primární číslo při výpočtu dopad balíčku jako, který by tomu bylo, že úspory uživatelé uvidí, když se zakážou rozšíření pro tento balíček.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Měření dopadu automaticky načíst rozšíření pomocí nástroje PerfView

Během analýzy kódu vám může pomoci identifikovat cesty kódu, které mohou zpomalit inicializace balíček, můžete také využít trasování pomocí aplikací, jako je PerfView na vědomí následky načtení balíčku v po spuštění sady Visual Studio.

PerfView je nástroj pro trasování celého systému. Tento nástroj vám problémových míst v aplikaci buď z důvodu využití procesoru nebo blokování systémových volání. Tady je krátká ukázka analýzy Ukázka rozšíření pomocí nástroje PerfView k dispozici na [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Příklad kódu:**

Tento příklad je založen na ukázkový kód níže, která je navržena k zobrazení malá a velká několik běžných příčin zpoždění:

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**Záznam trasování pomocí nástroje PerfView:**

Po nastavení prostředí sady Visual Studio pomocí rozšíření nainstalována, lze zaznamenat trasování spuštění otevřením PerfView a otevírání **shromažďovat** dialogu **shromažďovat** nabídky.

![shromažďování nabídky Nástroje perfview](media/perfview-collect-menu.png)

Výchozí možnosti poskytne zásobníky volání pro využití procesoru, ale od nás zajímají i času blokování, byste také měli povolit **vlákna čas** zásobníků. Jakmile jsou připravené nastavení můžete kliknout na **spustit shromažďování** a spuštění sady Visual Studio po zahájení nahrávání.

Před zastavením shromažďování, budete chtít Ujistěte se, že Visual Studio je plně inicializován, je zcela viditelné hlavní okno a pokud vaše rozšíření obsahuje všechny částí uživatelského rozhraní, které automaticky zobrazují, jsou také viditelné. Jakmile Visual Studio je zcela načten a inicializován rozšíření, můžete zastavit záznam analyzovat trasování.

**Analýza trasování pomocí nástroje PerfView:**

Po dokončení nahrávání PerfView automaticky otevřít sledování a možnosti $expand.

Pro účely tohoto příkladu nás zajímají hlavně **zásobníky vlákna čas** zobrazení, ve kterém najdete v části **skupinu rozšířené**. Toto zobrazení zobrazí celkový čas strávený na vlákně metodou včetně čas procesoru a čas zablokování, jako je například vstupně-výstupních operací disku nebo čeká na obslužné rutiny.

 ![zásobníky vlákna čas](media/perfview-thread-time-stacks.png)

 Při otevírání **zásobníky vlákna čas** zobrazit, měli byste zvolit **devenv** procesu se spustit analýzu.

PerfView obsahuje podrobné pokyny o tom, jak číst vlákno zásobníky čas v rámci své vlastní nabídky Nápověda pro podrobnější analýzu. Pro účely tohoto příkladu chceme vyfiltrovat pouze včetně zásobníků s vláknem naše balíčky modulu název a spuštění dále v tomto zobrazení.

1. Nastavte **GroupPats** na prázdný text odebrat seskupení nepřidají ve výchozím nastavení.
2. Nastavte **IncPats** zahrnout část názvu sestavení a spuštění vlákna kromě existující filtr procesu. V takovém případě by měl být **devenv; Spuštění podprocesu. MakeVsSlowExtension**.

Nyní zobrazí se pouze náklady spojené s sestavení týkající se rozšíření. V tomto zobrazení, podle kdykoli **Inc (včetně nákladů)** sloupec spuštění vlákna se vztahuje na naše filtrované rozšíření a bude mít vliv na spuštění.

Například výše některé zajímavé volání zásobníků by:

1. Vstupně-výstupních operací pomocí `System.IO` třída: celkové náklady na tyto snímky nemusí být moc drahé v trasování, ale jsou potenciální příčinou problému od souboru rychlost vstupně-výstupní operace se bude lišit počítač od počítače.

   ![vstupně-výstupních operací snímků systému](media/perfview-system-io-frames.png)

2. Blokovat čekání na jiné asynchronní práce volání: V tomto případě celkový čas představuje čas na dokončení asynchronní práce je blokován hlavního vlákna.

   ![blokování volání snímků](media/perfview-blocking-call-frames.png)

Jedna z ostatních zobrazení v trasování, které budou užitečné k určení vlivu se bude **Image zatížení zásobníky**. Můžete použít stejné filtry jako použitý pro **zásobníky vlákna čas** zobrazení a přečtěte si všechna sestavení načtená z důvodu prováděný balíčkem automaticky načíst kód.

Je důležité minimalizovat počet načtených sestavení v balíčku inicializační rutina jako každé další sestavení bude zahrnovat další diskových operací, které mohou zpomalit spuštění podstatně pomalejší počítačích.

## <a name="summary"></a>Souhrn

Po spuštění sady Visual Studio byl jeden z oblasti, které jsme neustále získat zpětnou vazbu. Naším cílem jak bylo uvedeno dříve, je pro všechny uživatele, aby konzistentní spouštění prostředí bez ohledu na to, komponenty a rozšíření, která jste nainstalovali. Rádi bychom se práce s vlastníky rozšíření, aby to pomohl ostatním Pomozte nám dosažení tohoto cíle. Výše uvedené pokyny by měl být užitečné pro pochopení vlivu rozšíření na spuštění a buď odpadá nutnost auto zatížení nebo načíst asynchronně k minimalizaci vlivu na produktivitu uživatelů.
