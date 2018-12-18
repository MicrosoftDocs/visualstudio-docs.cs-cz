---
title: Manifesty aplikace pro řešení pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9665be31a59de33713f981889bc8cb8a8cb55eea
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248173"
---
# <a name="application-manifests-for-office-solutions"></a>Manifesty aplikace pro řešení pro systém Office
  Manifest aplikace je soubor XML, který popisuje sestavení, která jsou načtena do jediného řešení Microsoft Office. Pomocí nástroje pro vývoj aplikace Microsoft Office v sadě Visual Studio [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] aplikace definované v manifestu schéma [ClickOnce – manifest aplikace](/visualstudio/deployment/clickonce-application-manifest) odkaz.  
  
 Manifesty aplikací pro Office řešení pomocí následujícího [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] elementů a atributů.  
  
|Prvek|Popis|Atributy|  
|-------------|-----------------|----------------|  
|[&#60;sestavení&#62; Element &#40;aplikace ClickOnce&#41;](/visualstudio/deployment/assembly-element-clickonce-deployment)|Povinný parametr. Element nejvyšší úrovně.|**ManifestVersion**|  
|[&#60;Vlastnost assemblyIdentity&#62; Element &#40;aplikace ClickOnce&#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment)|Povinný parametr. Identifikuje [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] primární sestavení aplikace.|**Jméno**<br /><br /> **version**<br /><br /> **PublicKeyToken**<br /><br /> **Vlastnost ProcessorArchitecture**<br /><br /> **Jazyk**|  
|[&#60;trustInfo&#62; Element &#40;aplikace ClickOnce&#41;](/visualstudio/deployment/trustinfo-element-clickonce-application)|Identifikuje požadavky na zabezpečení aplikace.|Žádná|  
|[&#60;vstupní bod&#62; Element &#40;aplikace ClickOnce&#41;](/visualstudio/deployment/entrypoint-element-clickonce-application)|Povinný parametr. Určuje vstupní bod aplikace kód pro spuštění.|**Jméno**<br /><br /> **dependencyName**<br /><br /> **customHostSpecified**|  
|[&#60;závislost&#62; Element &#40;aplikace ClickOnce&#41;](/visualstudio/deployment/dependency-element-clickonce-deployment)|Povinný parametr. Identifikuje každou závislost vyžaduje pro spuštění aplikace. Volitelně určuje sestavení, které je potřeba provést.|Žádné|  
|[&#60;soubor&#62; Element &#40;aplikace ClickOnce&#41;](/visualstudio/deployment/file-element-clickonce-application)|Požadováno. Identifikuje každý soubor bez sestavení, který používá aplikace. Izolace dat modelu COM (Component Object) přidružené k souboru může obsahovat.|**Jméno**<br /><br /> **Velikost**|  
  
 Manifesty aplikací pro řešení Office mají následující element v `co.v1` oboru názvů.  
  
```xml  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>   
```  
  
 Tyto manifesty aplikací také mít následující prvky a atributy v `vstav3` oboru názvů.  
  
```xml  
<addIn>  
  <entryPointsCollection>  
    <entryPoints>  
      <entryPoint>  
      </entryPoint>  
    </entryPoints>  
  </entryPointsCollection>  
  <update></update>  
  <postActions>  
    <postAction>  
      <postActionData>  
      </postActionData>  
    <postAction>  
  </postActions>  
  <application>  
    <customizations>  
      <customization>  
      </customization>  
    </customizations>  
  </application  
</addIn>  
```  
  
|Prvek|Popis|Atributy|  
|-------------|-----------------|----------------|  
|[&#60;customHostSpecified&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Povinný parametr. V manifestu označí konkrétně jako řešení pro Office.|Žádná|  
|[&#60;doplněk&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Povinný parametr. Vstupní body úložišť do jednoho oboru názvů.|Žádné|  
|[&#60;entrypointscollection –&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Povinný parametr. Seskupí všechna sestavení pro jeden nebo více řešení Office.|**id**|  
|[&#60;entryPoints&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Povinný parametr. Skupiny všechna sestavení ke spuštění řešení pro Office.|Žádná|  
|[&#60;vstupní bod&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Požadováno. Určuje sestavení ke spuštění v řešení pro Office.|**class**<br /><br /> **kontrakt**|  
|[&#60;Aktualizovat&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Povinný parametr. Nakonfiguruje aktualizace pro příslušné řešení.|**Povoleno**<br /><br /> **vypršení platnosti**|  
|[&#60;postactions –&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Volitelné. Seskupí všechny po nasazení akce, které se spustí po dokončení instalace řešení pro systém Office.|Žádná|  
|[&#60;postAction&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Volitelné. Určuje akci po nasazení.|Žádné|  
|[&#60;postactiondata –&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Volitelné. Nastaví data pro akci po nasazení.|Žádná|  
|[&#60;aplikace&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Požadováno. Zabalí informace specifické pro aplikaci do jednoho uzlu.|Žádné|  
|[&#60;přizpůsobení&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Povinný parametr. Ukládá všechny informace specifické pro hostitele aplikace v samostatných oborech názvů.|Žádné|  
|[&#60;přizpůsobení&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Požadováno. Ukládá informace specifické pro hostitele aplikace v samostatných oborech názvů.|**xmlns.**|  
|[&#60;dokument&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Vyžaduje se jenom pro řešení na úrovni dokumentu. Ukládá informace specifické pro přizpůsobení.|**solutionId**|  
|[&#60;appAddin&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Vyžaduje se jenom pro řešení na úrovni aplikace. Ukládá informace specifické pro přizpůsobení.|**Aplikace**<br /><br /> **LoadBehavior**<br /><br /> **Název klíče**|  
|[&#60;friendlyName&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Volitelné. Ukládá název VSTO doplněk, který se zobrazí v seznamu nainstalovaných doplňků VSTO.|Žádná|  
|[&#60;Popis&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Vyžaduje se jenom pro doplňky VSTO. Ukládá popis, který se zobrazí v seznamu nainstalovaných programů.|Žádná|  
|[&#60;formRegions&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Vyžaduje se jenom pro aplikaci Outlook doplňků VSTO, které zahrnují oblasti formuláře.|Žádná|  
|[&#60;formRegion&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Vyžaduje se jenom pro aplikaci Outlook doplňků VSTO, které zahrnují oblasti formuláře.|**Název**|  
|[&#60;vstoruntime –&#62; Element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Požadováno. Popisuje konkrétní verzi nástroje Visual Studio Tools for Office runtime, který podporuje řešení pro Office.|**Vydání verze**<br /><br /> **version**<br /><br /> **supportUrl**|  
  
## <a name="remarks"></a>Poznámky  
 Můžete ručně upravit aplikace a manifesty nasazení v řešeních pro systém Office. Později, musíte znovu podepsat aplikaci a manifesty nasazení s použitím Manifest Generation and Editing Tool (*mage.exe* a *mageui.exe*). Další informace najdete v tématu [jak: Znovu podepište manifesty aplikace a nasazení](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="file-location"></a>Umístění souboru  
 Manifest aplikace je specifická pro jednu verzi řešení. Z tohoto důvodu by měl být manifesty aplikací ukládají odděleně od manifesty nasazení. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Umístí soubory specifické pro verzi v podadresáři pojmenovaném přidružené verze v *soubory aplikace* podadresář ve složce publikování.  
  
## <a name="file-name-syntax"></a>Syntaxe názvu souboru  
 Název souboru manifestu aplikace by měl být úplný název a příponu aplikace v jsme uvedli, **assemblyIdentity** element, za nímž následuje rozšíření *.manifest*. Například manifest aplikace, která odkazuje *OutlookAddIn1.dll* přizpůsobení byste použili následující syntaxe názvu souboru.  
  
 `OutlookAddIn1.dll.manifest`  
  
## <a name="see-also"></a>Viz také:  
 [Manifesty nasazení pro řešení pro systém Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce – manifest aplikace](/visualstudio/deployment/clickonce-application-manifest)  
  
  