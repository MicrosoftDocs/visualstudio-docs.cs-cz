---
title: Ladění řešení služby SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6f53ca7f1a5e449d47a30a32967072f7220c159a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903150"
---
# <a name="debug-sharepoint-solutions"></a>Ladění řešení služby SharePoint
  Můžete ladit řešení služby SharePoint pomocí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ladicího programu. Při spuštění ladění, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nasadí soubory projektu pro SharePoint server a instanci webu služby SharePoint otevře ve webovém prohlížeči. Následující části popisují, jak ladit aplikace SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [Povolení ladění](#EnableDebug)  
  
-   [Proces nasazení a ladění F5](#Deployment)  
  
-   [Funkce projektu služby SharePoint](#Features)  
  
-   [Ladění pracovních postupů](#Workflow)  
  
-   [Ladění přijímačů událostí funkce](#FeatureEvents)  
  
-   [Povolení Rozšířené ladicí informace](#EnhancedDebug)  
  
## <a name="enable-debugging"></a>Povolení ladění
 Při prvním ladění řešení služby SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dialogové okno vás upozorní, že v souboru web.config není nakonfigurována pro povolení ladění. (V souboru web.config se vytvoří při instalaci serveru SharePoint. Další informace najdete v tématu [práce se soubory Web.config](http://go.microsoft.com/fwlink/?LinkID=149266).) Dialogové okno nabízí možnost buď spuštění projektu bez ladění nebo upravte soubor web.config pro povolení ladění. Pokud se rozhodnete první možnost, projekt běží normálně. Pokud se rozhodnete druhou možnost, v souboru web.config nastaven na:  
  
- Zapnout v zásobníku volání (`CallStack="true"`)  
  
- Zakázat vlastní chyby v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)  
  
- Povolit ladění kompilace (`<compilation debug="true">`)  
  
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
  
 Chcete-li změny a zakázat ladění, změňte následující [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] v souboru web.config:  
  
-   Vypnout zásobník volání (`CallStack="false"`)  
  
-   Povolit vlastní chyby v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)  
  
-   Zakázat ladění kompilace (`<compilation debug="false">`)  
  
## <a name="f5-debug-and-deployment-process"></a>Proces nasazení a ladění F5
 Při spuštění projektu služby SharePoint v režimu ladění, procesu nasazení Sharepointu provádí následující úlohy:  
  
1. Spouští přizpůsobitelné příkazy před nasazením.  
  
2. Vytvoří soubor balíčku (.wsp) webu řešení pomocí [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] příkazy. Soubor WSP obsahuje všechny potřebné soubory a funkce. Další informace najdete v tématu [přehled řešení](http://go.microsoft.com/fwlink/?LinkID=128154).  
  
3. Pokud řešení služby SharePoint je řešení farmy, recykluje [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] fondu aplikací pro určenou lokalitu [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]. Tento krok uvolní soubory uzamčené [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pracovní proces.  
  
4. Pokud předchozí verze balíčku už existuje, odvolá předchozí verzi funkce a soubory v souboru WSP. Tento krok deaktivuje funkce, odinstaluje balíček řešení a pak odstraní balíček řešení na serveru SharePoint.  
  
5. Nainstaluje aktuální verzi funkce a soubory v souboru WSP. Tento krok přidá a nainstaluje řešení na serveru SharePoint.  
  
6. Pro pracovní postupy nainstaluje sestavení pracovního postupu. Můžete změnit jeho umístění pomocí *umístění sestavení* vlastnost.  
  
7. Funkce v projektu v Sharepointu aktivuje, pokud obor je web nebo Web. Nemáte aktivaci funkce v oborech farmy a webovou aplikaci.  
  
8. Pro pracovní postupy, přidruží k knihovny služby SharePoint, seznamu nebo web, který jste vybrali v pracovním postupu **Průvodce přizpůsobením SharePoint**.  
  
   > [!NOTE]  
   >  Toto přidružení dojde pouze v případě, že jste vybrali **automaticky přidružení pracovního postupu** v průvodci.  
  
9. Spouští přizpůsobitelné příkazy po nasazení.  
  
10. Připojí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ladicí program se má [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] procesu (*w3wp.exe*). Pokud typ projektu můžete změnit *řešení v izolovaném prostoru* vlastnosti a její hodnota je nastavena na **true**, pak ladicí program připojí k jiným procesem (*SPUCWorkerProcess.exe*). Další informace najdete v tématu [aspekty řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).  
  
11. Spustí ladicí program jazyka JavaScript, pokud řešení služby SharePoint je řešení farmy.  
  
12. Zobrazí příslušnou knihovnu, seznamu nebo stránku ve webovém prohlížeči.  
  
    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Po dokončení každé úlohy se zobrazí stavová zpráva v okně výstup. Pokud úlohu nelze dokončit, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zobrazí chybovou zprávu v okně Seznam chyb.  
  
## <a name="sharepoint-project-features"></a>Funkcí projektu SharePoint
 Funkce je přenosné a modulární jednotka funkcí, které zjednodušuje úpravy sítí s použitím definice webu. Je také balíček [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] elementy (WSS), který můžete aktivovat pro konkrétní obor a který umožňuje uživatelům provádět určité cíle nebo úkolu. Šablony jsou nasazeny jako funkce.  
  
 Při spuštění projektu v režimu ladění, proces nasazení vytvoří složku v *funkce* adresáře v *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES*. Názvy funkcí mají formát *název projektu*_funkcí*x*, jako je například TestProject_Feature1.  
  
 Obsahuje složky řešení v adresáři funkce *definice funkce* souboru a *definice pracovního postupu* souboru. Soubor definic funkcí (Feature.xml) popisuje soubory v projektu Feature.The projektu definičním souboru (*Elements.xml*) popisuje šablony projektu. *Elements.xml* lze nalézt v **Průzkumníka řešení**, ale Feature.xml se vygeneruje, když je vytvořen balíček řešení. Další informace o těchto souborech najdete v tématu [SharePoint šablony položek projektu a projekt](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
## <a name="debug-workflows"></a>Ladění pracovních postupů
 Při ladění projektů pracovních postupů [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá šablona pracovního postupu (v závislosti na jeho typu) do knihovny nebo do seznamu. Šablona pracovního postupu potom lze spustit ručně nebo pomocí přidání nebo aktualizaci položky. Pak můžete použít [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ladění pracovního postupu.  
  
> [!NOTE]
>  Pokud chcete přidat odkazy na jiná sestavení, ujistěte se, že tato sestavení jsou nainstalované v globální mezipaměti sestavení ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). V opačném případě se nezdaří řešení pracovního postupu. Informace o postupu při instalaci sestavení naleznete v tématu [ručně spustit pracovní postup na dokument nebo položku](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).  
  
 Proces nasazení, ale nespustí pracovního postupu. Pracovní postup je nutné spustit z webu služby SharePoint. Pracovní postup můžete spustit také pomocí klientské aplikace, jako je například Microsoft Office Word 2010, nebo pomocí samostatného kódu na straně serveru. Použijte jeden z přístupů podle **Průvodce přizpůsobením SharePoint**.  
  
 Například pokud jste zadali, že můžete pracovní postup spuštěn ručně, spusťte pracovní postup přímo z položky v seznamu nebo knihovně. Další informace o tom, jak spustit pracovní postup ručně, najdete v části [ručně spustit pracovní postup pro položku dokumentu](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).  
  
## <a name="debug-feature-event-receivers"></a>Ladění přijímačů událostí funkce
 Ve výchozím nastavení při spuštění [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikace služby SharePoint, jeho funkce jsou automaticky aktivovány pro vás na Sharepointovém serveru. Ale to způsobí, že problémy při ladění přijímačů událostí funkce, protože když se funkce aktivuje podle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], poběží v jiného procesu než ladicí program. To znamená, že některé funkce ladění, jako například zarážky, nebudou fungovat správně.  
  
 Chcete-li zakázat automatickou aktivaci funkce v Sharepointu a povolit správné ladění přijímačů událostí funkce, nastavte hodnotu projektu **aktivní konfigurace nasazení** vlastnost **bez aktivace** před laděním. Poté, po spuštění ladění aplikace SharePoint ve [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], je nutné ručně aktivovat funkci v Sharepointu. Chcete-li aktivovat tuto funkci, otevřete **Akce webu** nabídku v Sharepointu, zvolte **nastavení webu**, zvolte **spravovat funkce webu** propojit a klikněte na tlačítko **Aktivovat** tlačítko vedle funkcí, pro pokračování v ladění jako obvykle.  
  
## <a name="enable-enhanced-debug-information"></a>Informace o povolení rozšířeného ladění
 Z důvodu někdy složité interakce mezi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] procesu (devenv.exe) [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hostitelském procesu Sharepointu (*vssphost4.exe*), SharePoint a vrstvě WCF Diagnostika chyb, ke kterým dochází při sestavování, nasazování a tak dále, může být náročné. Abyste mohli tyto chyby vyřešit, můžete povolit rozšířené ladicí informace. Chcete-li to provést, přejděte na následující klíč registru v registru Windows:  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**  
  
 Pokud "EnableDiagnostics" **REG_DWORD** hodnotu ještě neexistuje, vytvořte ji ručně. Nastavte hodnotu "EnableDiagnostics" na "1".  
  
 Nastavením tohoto klíče hodnotu 1 způsobí, že zásobník informace se zobrazí v trasování **výstup** okna pokaždé, když dojde k chybě systému projektu, při spuštění [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Zakázat rozšířené ladicí informace, nastavte EnableDiagnostics zpět na 0 nebo odstraňte hodnotu.  
  
 Další informace o jiných klíčů registru služby SharePoint, naleznete v tématu [rozšíření pro nástroje služby SharePoint v sadě Visual Studio pro ladění](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Viz také:
 [Řešení potíží s řešeními služby SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
