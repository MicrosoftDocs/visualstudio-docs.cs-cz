---
title: '&lt;&gt;element nasazení (nasazení ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a55b5519d5abb7b40aeca23fed1bc2f8ea2cc33d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194644"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;&gt;element nasazení (nasazení ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje atributy používané pro nasazení aktualizací a expozici systému.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `deployment`Element je povinný a je v `urn:schemas-microsoft-com:asm.v1` oboru názvů. Element má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`install`|Povinná hodnota. Určuje, zda tato aplikace definuje přítomnost v nabídce **Start** systému Windows a v Ovládacích panelech aplikace **Přidat nebo odebrat programy** . Platné hodnoty jsou `true` a `false` . Pokud `false` , [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bude vždy spouštět nejnovější verzi této aplikace ze sítě a nebude rozpoznána `subscription` element.|  
|`minimumRequiredVersion`|Nepovinný parametr. Určuje minimální verzi této aplikace, která se dá spustit na klientovi. Pokud je číslo verze aplikace menší než číslo verze uvedené v manifestu nasazení, aplikace se nespustí. Čísla verzí musí být zadána ve formátu `N.N.N.N` , kde `N` je unsigned integer. Pokud `install` je atribut `false` , `minimumRequiredVersion` nesmí být nastaven.|  
|`mapFileExtensions`|Nepovinný parametr. Výchozí hodnota je `false` . Pokud `true` všechny soubory v nasazení musí mít příponu. deploy. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Tato rozšíření odeberou tyto soubory ihned po jejich stažení z webového serveru. Pokud publikujete aplikaci pomocí nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , toto rozšíření automaticky přidá do všech souborů. Tento parametr umožňuje stažení všech souborů v rámci [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení z webového serveru, který blokuje přenos souborů končících "nebezpečné" přípony, jako je například. exe.|  
|`disallowUrlActivation`|Nepovinný parametr. Výchozí hodnota je `false` . Pokud `true` , zabrání spuštění nainstalované aplikace kliknutím na adresu URL nebo zadáním adresy URL do aplikace Internet Explorer. Pokud `install` atribut není přítomen, je tento atribut ignorován.|  
|`trustURLParameters`|Nepovinný parametr. Výchozí hodnota je `false` . Pokud `true` umožňuje, aby adresa URL obsahovala parametry řetězce dotazu, které jsou předány do aplikace, podobně jako argumenty příkazového řádku jsou předány do aplikace příkazového řádku. Další informace naleznete v tématu [How to: načíst informace řetězce dotazu v online aplikaci ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Pokud `disallowUrlActivation` je atribut `true` , `trustUrlParameters` musí být buď vyloučen z manifestu, nebo explicitně nastaven na `false` .|  
  
 `deployment`Element také obsahuje následující podřízené prvky.  
  
## <a name="subscription"></a>předplatné  
 Nepovinný parametr. Obsahuje `update` element. `subscription`Element nemá žádné atributy. Pokud `subscription` element neexistuje, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace nebude nikdy vyhledávat aktualizace. Pokud `install` `deployment` je atribut elementu, je `false` `subscription` ignorován, protože [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace, která je spuštěna ze sítě, vždy používá nejnovější verzi.  
  
## <a name="update"></a>update  
 Povinná hodnota. Tento prvek je podřízeným `subscription` prvkem prvku a obsahuje buď prvek, `beforeApplicationStartup` nebo `expiration` . `beforeApplicationStartup` a `expiration` nemohou být současně zadány ve stejném manifestu nasazení.  
  
 `update`Element nemá žádné atributy.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 Nepovinný parametr. Tento prvek je podřízeným `update` prvkem prvku a nemá žádné atributy. Když `beforeApplicationStartup` prvek existuje, aplikace se zablokuje při [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] kontrole aktualizací, pokud je klient online. Pokud tento prvek neexistuje, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bude nejprve vyhledávat aktualizace na základě hodnot zadaných pro `expiration` element. `beforeApplicationStartup` a `expiration` nemohou být současně zadány ve stejném manifestu nasazení.  
  
## <a name="expiration"></a>vypršení platnosti  
 Nepovinný parametr. Tento prvek je podřízený `update` elementu a nemá žádné podřízené položky. `beforeApplicationStartup` a `expiration` nemohou být současně zadány ve stejném manifestu nasazení. Když dojde k ověření aktualizace a zjištěna aktualizovaná verze, nová verze mezipaměti se spustí, když je spuštěná stávající verze. Nová verze se pak nainstaluje při dalším spuštění [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace.  
  
 `expiration`Element podporuje následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`maximumAge`|Povinná hodnota. Určuje, jak starý má aktuální aktualizace dojít předtím, než aplikace provede kontrolu aktualizace. Časová jednotka je určena `unit` atributem.|  
|`unit`|Povinná hodnota. Určuje jednotku času pro `maximumAge` . Platné jednotky jsou `hours` , `days` a `weeks` .|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 Pro .NET Framework 2,0 je tento element požadován, pokud manifest nasazení obsahuje `subscription` oddíl. Pro .NET Framework 3,5 a novější je tento prvek volitelný a bude ve výchozím nastavení použita cesta k serveru a souboru, ve kterém byl nalezen manifest nasazení.  
  
 Tento prvek je podřízeným `deployment` prvkem prvku a má následující atribut.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`codebase`|Povinná hodnota. Označuje umístění manifestu nasazení, který se používá k aktualizaci aplikace, jako identifikátor URI (Uniform Resource Identifier) [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Tento prvek také umožňuje předávat umístění aktualizací pro instalace založené na CD. Musí se jednat o platný identifikátor URI.|  
  
## <a name="remarks"></a>Poznámky  
 Aplikaci můžete nakonfigurovat [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tak, aby hledala aktualizace při spuštění, kontrolovala aktualizace po spuštění nebo nikdy nekontrolovala aktualizace. Chcete-li vyhledat aktualizace při spuštění, zajistěte, aby `beforeApplicationStartup` element existoval v rámci `update` elementu. Chcete-li vyhledat aktualizace po spuštění, ujistěte se, že `expiration` element existuje pod `update` prvkem a že jsou k dispozici intervaly aktualizací.  
  
 Chcete-li zakázat kontrolu aktualizací, odeberte `subscription` prvek. Pokud zadáte v manifestu nasazení, aby nikdy nehledaly aktualizace, můžete k ruční kontrole aktualizací použít <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> metodu.  
  
 Další informace o tom, jak se deploymentProvider vztahuje na aktualizace, najdete v tématu [volba strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Příklady  
 Následující příklad kódu ukazuje `deployment` prvek v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu nasazení. V příkladu se používá `deploymentProvider` element k označení upřednostňovaného umístění aktualizace.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)
