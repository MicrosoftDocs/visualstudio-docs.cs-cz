---
title: Manifesty aplikace pro řešení Office
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a6272f145ee2c7ef2a91cc635112e440e6404457
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531505"
---
# <a name="application-manifests-for-office-solutions"></a>Manifesty aplikace pro řešení Office
  Manifest aplikace je soubor XML, který popisuje sestavení, která jsou načtena do řešení systém Microsoft Office. Vývojové nástroje systém Microsoft Office v aplikaci Visual Studio používají [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] schéma manifestu aplikace definované v referenčních informacích k [manifestu aplikace ClickOnce](../deployment/clickonce-application-manifest.md) .

 Manifesty aplikace pro řešení Office používají následující [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] prvky a atributy.

|Element|Popis|Atributy|
|-------------|-----------------|----------------|
|[&#60;&#62; sestavení elementu &#40;aplikace ClickOnce&#41;](../deployment/assembly-element-clickonce-deployment.md)|Povinná hodnota. Element nejvyšší úrovně.|**manifestVersion**|
|[&#60;assemblyIdentity&#62; elementu &#40;aplikace ClickOnce&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|Povinná hodnota. Identifikuje [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] primární sestavení aplikace.|**Jméno**<br /><br /> **znění**<br /><br /> **publicKeyToken**<br /><br /> **processorArchitecture**<br /><br /> **Language**|
|[&#60;trustInfo&#62; elementu &#40;aplikace ClickOnce&#41;](../deployment/trustinfo-element-clickonce-application.md)|Určuje požadavky na zabezpečení aplikace.|Žádné|
|[&#62; elementu&#60;entryPoint &#40;aplikace ClickOnce&#41;](../deployment/entrypoint-element-clickonce-application.md)|Povinná hodnota. Identifikuje vstupní bod kódu aplikace pro provedení.|**Jméno**<br /><br /> **Dependency**<br /><br /> **customHostSpecified**|
|[&#60;&#62; element závislosti &#40;aplikace ClickOnce&#41;](../deployment/dependency-element-clickonce-deployment.md)|Povinná hodnota. Identifikuje každou závislost nutnou ke spuštění aplikace. Volitelně identifikuje sestavení, která musí být předinstalována.|Žádné|
|[&#60;&#62; elementu &#40;aplikace ClickOnce&#41;](../deployment/file-element-clickonce-application.md)|Povinná hodnota. Identifikuje každý soubor bez sestavení, který je používán aplikací. Může zahrnovat data izolace modelu COM (Component Object Model) přidružená k souboru.|**Jméno**<br /><br /> **hodnota**|

 Manifesty aplikace pro řešení Office mají v oboru názvů následující element `co.v1` .

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

 Tyto manifesty aplikace mají také následující elementy a atributy v `vstav3` oboru názvů.

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

|Element|Popis|Atributy|
|-------------|-----------------|----------------|
|[&#60;customHostSpecified&#62; element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Povinná hodnota. Označí manifest specificky jako řešení pro Office.|Žádné|
|[&#62; element&#60;AddIn &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Povinná hodnota. Ukládá vstupní body do jednoho oboru názvů.|Žádné|
|[&#60;entryPointsCollection&#62; element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Povinná hodnota. Seskupí všechna sestavení pro jedno nebo více řešení pro systém Office.|**id**|
|[&#60;entryPoint&#62; elementu &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Povinná hodnota. Seskupí všechna sestavení pro spuštění řešení Office.|Žádné|
|[&#62; elementu&#60;entryPoint &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Povinná hodnota. Identifikuje sestavení pro spuštění v řešení pro systém Office.|**Deník**<br /><br /> **dodavatele**|
|[&#60;Update&#62; elementu &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Povinná hodnota. Nakonfiguruje aktualizace pro řešení.|**umožněn**<br /><br /> **vypršení platnosti**|
|[&#60;postActions&#62; element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Nepovinný parametr. Seskupí všechny akce po nasazení, které se spouštějí po instalaci řešení Office.|Žádné|
|[&#60;postAction&#62; element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Nepovinný parametr. Identifikuje akci po nasazení.|Žádné|
|[&#60;postActionData&#62; element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Nepovinný parametr. Konfiguruje data pro akci po nasazení.|Žádné|
|[&#60;&#62; element aplikace &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Povinná hodnota. Zabalí informace specifické pro aplikaci do jednoho uzlu.|Žádné|
|[&#60;přizpůsobení&#62; elementu &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Povinná hodnota. Ukládá všechny informace specifické pro hostitele aplikace v samostatném oboru názvů.|Žádné|
|[&#60;přizpůsobení&#62; elementu &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Povinná hodnota. Ukládá informace specifické pro hostitele aplikace v samostatném oboru názvů.|**xmlns**|
|[&#60;dokumentu&#62; element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Vyžaduje se jenom pro řešení na úrovni dokumentu. Ukládá informace specifické pro přizpůsobení.|**solutionId**|
|[&#60;appAddin&#62; element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Vyžaduje se jenom pro řešení na úrovni aplikace. Ukládá informace specifické pro přizpůsobení.|**aplikace**<br /><br /> **loadBehavior**<br /><br /> **Klíče**|
|[&#60;elementu friendlyName&#62; &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Nepovinný parametr. Ukládá název doplňku VSTO, který se zobrazí v seznamu nainstalovaných doplňků VSTO.|Žádné|
|[&#60;Description&#62; element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Vyžaduje se jenom pro doplňky VSTO. Ukládá popis, který se zobrazí v seznamu nainstalovaných programů.|Žádné|
|[&#60;formRegions&#62; element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Vyžaduje se jenom pro doplňky Outlook VSTO, které obsahují oblasti formulářů.|Žádné|
|[&#60;formRegion&#62; element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Vyžaduje se jenom pro doplňky Outlook VSTO, které obsahují oblasti formulářů.|**Name**|
|[&#60;vstoRuntime&#62; element &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Povinná hodnota. Popisuje specifickou verzi modulu runtime Visual Studio Tools for Office, který je podporován řešením Office.|**předběžné**<br /><br /> **znění**<br /><br /> **supportUrl**|

## <a name="remarks"></a>Poznámky
 V řešeních pro systém Office můžete ručně upravovat manifesty aplikací a nasazení. Následně je nutné znovu podepsat manifest aplikace a nasazení pomocí Manifest Generation and Editing Tool (*mage.exe* a *mageui.exe*). Další informace najdete v tématu [Postup: Opětovné podepsání manifestů aplikace a nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="file-location"></a>Umístění souboru
 Manifest aplikace je specifický pro jednu verzi řešení. Z tohoto důvodu by manifesty aplikací měly být uloženy odděleně od manifestů nasazení. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umístí soubory specifické pro danou verzi do podadresáře s názvem po přidružené verzi v podadresáři *soubory aplikace* ve složce pro publikování.

## <a name="file-name-syntax"></a>Syntaxe názvu souboru
 Název souboru manifestu aplikace by měl být úplný název a přípona aplikace, jak je uvedeno v prvku **assemblyIdentity** a následuje přípona *. manifest*. Například manifest aplikace, který odkazuje na přizpůsobení *OutlookAddIn1.dll* , by používal následující syntaxi názvu souboru.

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>Viz také

- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)