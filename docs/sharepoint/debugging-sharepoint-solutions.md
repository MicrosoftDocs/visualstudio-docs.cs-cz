---
title: Ladění řešení služby SharePoint | Microsoft Docs
description: Ladění řešení služby SharePoint pomocí ladicího programu sady Visual Studio. Prozkoumejte proces ladění a nasazení F5, ladit pracovní postupy a ladit přijímače událostí funkcí.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f1a6abfbafcbafb9daa52fdc6af85156700efef7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948944"
---
# <a name="debug-sharepoint-solutions"></a>Ladění řešení služby SharePoint
  Můžete ladit řešení služby SharePoint pomocí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ladicího programu. Když spustíte ladění, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nasadí soubory projektu na server SharePoint a pak otevře instanci webu služby SharePoint ve webovém prohlížeči. Následující části vysvětlují, jak ladit aplikace služby SharePoint v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [Povolení ladění](#enable-debugging)

- [Proces ladění a nasazení F5](#f5-debug-and-deployment-process)

- [Funkce SharePointového projektu](#sharepoint-project-features)

- [Ladění pracovních postupů](#debug-workflows)

- [Ladit přijímače událostí funkcí](#debug-feature-event-receivers)

- [Povolit ladicí informace ehanced](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>Povolení ladění
 Při prvním ladění řešení služby SharePoint v nástroji se zobrazí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dialogové okno s upozorněním, že soubor web.config není nakonfigurován pro povolení ladění. (Soubor web.config se vytvoří při instalaci serveru SharePoint Server. Další informace najdete v tématu [práce s Web.config soubory](/previous-versions/office/developer/sharepoint-2010/ms460914(v=office.14)).) Dialogové okno poskytuje možnost buď spustit projekt bez ladění, nebo úpravou souboru web.config pro povolení ladění. Pokud zvolíte první možnost, projekt se spustí normálně. Pokud zvolíte druhou možnost, web.config soubor je nakonfigurován na:

- Zapnout zásobník volání ( `CallStack="true"` )

- Zakázat vlastní chyby v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ( `<customErrors mode="Off" />` )

- Povolit ladění kompilace ( `<compilation debug="true">` )

  Výsledný soubor web.config následující:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <configuration>
        ...
        <SharePoint>
            <SafeMode MaxControls="200"
                CallStack="true"
                DirectFileDependencies="10"
                TotalFileDependencies="50"
                AllowPageLevelTrace="false">
                ...
            </SafeMode>
        ...
        </SharePoint>
        <system.web>
            ...
            <customErrors mode="Off" />
            ...
            <compilation debug="true">
            ...
            </compilation>
            ...
        </system.web>
        ...
    </configuration>
```

 Chcete-li změny vrátit zpět a zakázat ladění, změňte [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] v souboru web.config následující:

- Vypnutí zásobníku volání ( `CallStack="false"` )

- Povolit vlastní chyby v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ( `<customErrors mode="On" />` )

- Zakázat ladění kompilace ( `<compilation debug="false">` )

## <a name="f5-debug-and-deployment-process"></a>Proces ladění a nasazení F5
 Při spuštění projektu služby SharePoint v režimu ladění provede proces nasazení služby SharePoint následující úlohy:

1. Spustí přizpůsobitelné příkazy před nasazením.

2. Vytvoří soubor balíčku webové řešení (. wsp) pomocí [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] příkazů. Soubor. wsp obsahuje všechny nezbytné soubory a funkce. Další informace najdete v tématu [Přehled řešení](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

3. Pokud je řešením služby SharePoint řešení farmy, recykluje [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] fond aplikací pro zadanou lokalitu [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] . Tento krok uvolňuje soubory uzamčené [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pracovním procesem.

4. Pokud již existuje předchozí verze balíčku, odvolá předchozí verzi funkcí a souborů v souboru. wsp. Tento krok deaktivuje funkce, odinstaluje balíček řešení a pak odstraní balíček řešení na SharePointovém serveru.

5. Nainstaluje aktuální verzi funkcí a souborů v souboru. wsp. Tento krok přidá a nainstaluje řešení na SharePointový Server.

6. Pro pracovní postupy nainstaluje sestavení pracovního postupu. Jeho umístění můžete změnit pomocí vlastnosti *umístění sestavení* .

7. Aktivuje funkci projektu na SharePointu, pokud je oborem web nebo Web. Funkce v oborech Farm a WebApplication nejsou aktivovány.

8. U pracovních postupů přidruží pracovní postup k knihovně, seznamu nebo webu služby SharePoint, kterou jste vybrali v **Průvodci vlastním nastavením služby SharePoint**.

   > [!NOTE]
   > K tomuto přidružení dojde pouze v případě, že jste v průvodci vybrali možnost **automaticky přidružit pracovní postup** .

9. Spustí přizpůsobitelné příkazy po nasazení.

10. Připojí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ladicí program k [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] procesu (*w3wp.exe*). Pokud typ projektu umožňuje změnit vlastnost řešení v *izolovaném prostoru* a jeho hodnotu je nastavena na **hodnotu true**, ladicí program se připojí k jinému procesu (*SPUCWorkerProcess.exe*). Další informace najdete v tématu [požadavky na řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).

11. Spustí ladicí program JavaScriptu, pokud je řešením služby SharePoint řešení farmy.

12. Zobrazí ve webovém prohlížeči příslušnou knihovnu, seznam nebo stránku webu.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Po dokončení každé úlohy zobrazí stavovou zprávu v okně výstup. Pokud úlohu nelze dokončit, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zobrazí se v okně Seznam chyb chybová zpráva.

## <a name="sharepoint-project-features"></a>Funkce SharePointového projektu
 Funkce je přenosná a modulární jednotka funkcí, která zjednodušuje úpravu lokalit pomocí definic webů. Také se jedná o prvky balíčku [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS), které je možné aktivovat pro konkrétní obor a které pomáhají uživatelům provádět konkrétní cíl nebo úlohu. Šablony se nasazují jako funkce.

 Při spuštění projektu v režimu ladění vytvoří proces nasazení složku v adresáři *funkce* na adrese *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES*. Názvy funkcí mají formát *název projektu* _Feature *x*, například TestProject_Feature1.

 Složka řešení v adresáři funkcí obsahuje soubor *definice funkce* a soubor *definice pracovního postupu* . Definiční soubor funkce (Feature.xml) popisuje soubory ve funkci projektu. definiční soubor projektu (*Elements.xml*) popisuje šablonu projektu. *Elements.xml* lze nalézt v **Průzkumník řešení**, ale při vytvoření balíčku řešení se vygeneruje Feature.xml. Další informace o těchto souborech naleznete v tématu [šablony projektů a položek projektu služby SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

## <a name="debug-workflows"></a>Ladění pracovních postupů
 Když ladíte projekty pracovního postupu, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá šablonu pracovního postupu (v závislosti na jejím typu) do knihovny nebo do seznamu. Šablonu pracovního postupu pak můžete spustit ručně nebo přidáním nebo aktualizací položky. Pak můžete použít [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] k ladění pracovního postupu.

> [!NOTE]
> Pokud přidáte odkazy na jiná sestavení, ujistěte se, že jsou tato sestavení nainstalována v globální mezipaměti sestavení ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] ). V opačném případě se řešení pracovního postupu nezdaří. Informace o tom, jak nainstalovat sestavení, naleznete v tématu [Ruční spuštění pracovního postupu pro dokument nebo položku](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

 Proces nasazení ale pracovní postup nespustí. Pracovní postup je nutné spustit z webu služby SharePoint. Pracovní postup můžete spustit také pomocí klientské aplikace, jako je například systém Microsoft Office Word 2010, nebo pomocí samostatného kódu na straně serveru. Použijte jeden z přístupů uvedených v **Průvodci vlastním nastavením služby SharePoint**.

 Pokud jste například zadali, že pracovní postup lze spustit ručně, spusťte pracovní postup přímo z položky v knihovně nebo seznamu. Další informace o tom, jak ručně spustit pracovní postup, najdete v tématu [Ruční spuštění pracovního postupu pro položku dokumentu](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

## <a name="debug-feature-event-receivers"></a>Ladit přijímače událostí funkcí
 Ve výchozím nastavení se při spuštění [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikace služby SharePoint automaticky aktivuje její funkce na sharepointovém serveru. To však způsobuje problémy při ladění přijímačů událostí funkce, protože když je funkce aktivována nástrojem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , běží v jiném procesu než ladicí program. To znamená, že některé funkce ladění, například zarážky, nebudou pracovat správně.

 Chcete-li zakázat automatickou aktivaci funkce ve službě SharePoint a povolit správné ladění přijímačů událostí funkce, nastavte hodnotu vlastnosti **Konfigurace aktivního nasazení** projektu na možnost **bez aktivace** před laděním. Po zahájení ladění aplikace služby SharePoint v aplikaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ručně aktivujte funkci služby SharePoint. Pokud chcete aktivovat tuto funkci, otevřete nabídku **Akce webu** na SharePointu, zvolte **nastavení lokality**, zvolte odkaz **Spravovat funkce lokality** a pak zvolte tlačítko **aktivovat** vedle funkce, aby se ladění dalo normální.

## <a name="enable-enhanced-debugging-information"></a>Povolit rozšířené informace o ladění
 Z důvodu občas složitých interakcí mezi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] procesem (devenv.exe), [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hostitelským procesem služby sharepoint (*vssphost4.exe*), serverem SharePoint a vrstvou WCF se při diagnostice chyb, ke kterým dochází při sestavování, nasazování a tak dále, může jednat o výzvu. Abychom vám pomohli tyto chyby vyřešit, můžete povolit rozšířené ladicí informace. Provedete to tak, že v registru systému Windows přejdete na následující klíč registru:

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 Pokud hodnota **REG_DWORD** EnableDiagnostics ještě neexistuje, vytvořte ji ručně. Nastavte hodnotu "EnableDiagnostics" na "1".

 Nastavení této hodnoty klíče na hodnotu 1 způsobí, že se informace o trasování zásobníku zobrazí v okně **výstup** vždy, když dojde k chybám systému projektu při spuštění v produktu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Chcete-li zakázat rozšířené informace o ladění, nastavte EnableDiagnostics zpět na 0 nebo tuto hodnotu odstraňte.

 Další informace o dalších klíčích registru služby SharePoint naleznete v tématu [rozšíření ladění pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Řešení potíží s řešeními služby SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)
