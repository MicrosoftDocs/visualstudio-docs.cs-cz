---
title: '&lt;vstupní bod&gt; – Element (aplikace ClickOnce) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: da308de644dfc73d9364b65e21e820d6fc6c2a8a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255309"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;vstupní bod&gt; – Element (aplikace ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje sestavení, které by měla být spuštěna při to [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] na klientském počítači při spuštění aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `entryPoint` Element je povinný a je v `urn:schemas-microsoft-com:asm.v2` oboru názvů. Může existovat jenom jeden `entryPoint` element definovaný v manifestu aplikace.  
  
 `entryPoint` Element má tento atribut.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Volitelné. Tato hodnota se používá rozhraní .NET Framework.|  
  
 `entryPoint` obsahuje následující prvky.  
  
## <a name="assemblyidentity"></a>Vlastnost assemblyIdentity  
 Požadováno. Role `assemblyIdentity` a jeho atributy jsou definovány v [ \<assemblyIdentity > Element](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 `processorArchitecture` Atribut tohoto elementu a `processorArchitecture` atributu definovanému v `assemblyIdentity` jinde v aplikaci musí odpovídat manifestu.  
  
## <a name="commandline"></a>příkazový řádek  
 Požadováno. Musí být podřízeným `entryPoint` elementu. Nemá žádný podřízený element a má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`file`|Požadováno. Místní reference na sestavení po spuštění pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace. Tato hodnota nemůže obsahovat lomítko (/) nebo zpětné lomítko (\\) oddělovače cest.|  
|`parameters`|Požadováno. Popisuje akce má být provedena se vstupním bodem. Jediná platná hodnota je `run`; Pokud je zadán prázdný řetězec, `run` se předpokládá, že.|  
  
## <a name="customhostrequired"></a>customHostRequired  
 Volitelné. Pokud zahrnuty, určuje, zda toto nasazení obsahuje komponenty, která se nasadí v rámci vlastního hostitele a není samostatné aplikace.  
  
 Pokud tento prvek je k dispozici, `assemblyIdentity` a `commandLine` elementy nesmí být také k dispozici. Pokud jsou, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vyvolá chybu ověření během instalace.  
  
 Tento element nemá žádné atributy a podřízené prvky.  
  
## <a name="customux"></a>customUX  
 Volitelné. Určuje, že aplikace je nainstalovaná a udržuje vlastní instalační program a není vytvořit položku nabídky Start, místní nebo přidat nebo odebrat programy.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Aplikace, která obsahuje customUX element musí poskytnout vlastní instalační program, který používá <xref:System.Deployment.Application.InPlaceHostingManager> instalace pro provádění operací. Aplikace s tímto elementem není nainstalovat poklepáním na jeho zaváděcí manifestu nebo setup.exe. Vlastní instalační program můžete vytvořit položky nabídky Start, zástupce a položky panelu Přidat nebo odebrat programy. Pokud vlastní instalační program nevytvoří záznam přidat nebo odebrat programy, musí ukládat identifikátor předplatného poskytované <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> vlastnost a povolit uživatele pro odinstalaci aplikace později voláním <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> metody. Další informace najdete v tématu [návod: vytvoření vlastního instalátoru pro aplikaci ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek určuje sestavení a vstupní bod pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace.  
  
 Nemůžete použít `commandLine` pro předání parametrů do vaší aplikace v době běhu. Parametry řetězce dotazu pro dostanete [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení z vaší aplikace <xref:System.AppDomain>. Další informace najdete v tématu [postupy: načtení informací řetězce dotazu do Online aplikace ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `entryPoint` elementu v manifestu aplikace pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace. Tento příklad kódu je součástí většího příkladu určeného pro [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md) tématu.  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – manifest aplikace ](../deployment/clickonce-application-manifest.md)



