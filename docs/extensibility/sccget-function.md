---
title: Sccget – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3955905252b2293d3c200640ea33d5c23c8fd208
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844455"
---
# <a name="sccget-function"></a>Sccget – funkce
Tato funkce načte kopii jeden nebo více souborů pro zobrazení a kompilace, ale ne pro úpravy. Ve většině systémů jsou soubory označené jako jen pro čtení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontext modulu plug-in správy zdrojového kódu.  
  
 hWnd  
 [in] Popisovač okna integrovaného vývojového prostředí, které modul plug-in správy zdrojového kódu můžete použít jako nadřazený pro všechna dialogová okna, které poskytuje.  
  
 %{nfiles/  
 [in] Počet souborů podle `lpFileNames` pole.  
  
 lpFileNames  
 [in] Pole plně kvalifikované názvy souborů, které se mají načíst.  
  
 fOptions  
 [in] Příkaz příznaky (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 pvOptions  
 [in] Možností správy zdrojového kódu plug-konkrétní.  
  
## <a name="return-value"></a>Návratová hodnota  
 Modul plug-in implementaci ovládacího prvku zdroje této funkce má vracet instanci jednoho z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Úspěšné operaci get.|  
|SCC_E_FILENOTCONTROLLED|Soubor není pod správou zdrojových kódů.|  
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu nepodporuje tuto operaci.|  
|SCC_E_FILEISCHECKEDOUT|Nelze získat soubor, který uživatel aktuálně rezervoval.|  
|SCC_E_ACCESSFAILURE|Došlo k problému, přístup k systému správy zdrojového kódu, pravděpodobně kvůli problémům se síti nebo kolize. Doporučuje se zkuste to znovu.|  
|SCC_E_NOSPECIFIEDVERSION|Zadali jste neplatnou verzi nebo datum a čas.|  
|SCC_E_NONSPECIFICERROR|Obecná chyba; Soubor nebyl synchronizován.|  
|SCC_I_OPERATIONCANCELED|Operace zrušena před dokončením.|  
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je volána s počet a pole názvů souborů, které se mají načíst. Pokud rozhraní IDE předává příznak `SCC_GET_ALL`, to znamená, že položky v `lpFileNames` nejsou soubory, ale adresářů a že všechny soubory pod správou zdrojových kódů v daném adresáři se mají načíst.  
  
 `SCC_GET_ALL` Příznak je možné kombinovat s `SCC_GET_RECURSIVE` příznak načíst všechny soubory v daném adresáři a všech jeho podadresářích.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` měl by být nikdy předán bez `SCC_GET_ALL`. Všimněte si také, že pokud adresáře *C:\A* a *C:\A\B* jsou předány v rekurzivní get, *C:\A\B* a všechny jeho podadresáře budou načítat skutečně dvakrát. Zodpovídá za rozhraní IDE, a ne zdrojový ovládací prvek modulu plug-in – abyste měli jistotu, že duplicitní položky, jako je například tento uchovávají mimo pole.  
  
 Nakonec i v případě, že modul plug-in správy zdrojových kódů zadaný `SCC_CAP_GET_NOUI` příznak při inicializaci, která udává, že nemá žádné uživatelské rozhraní pro příkaz Get, tato funkce může stále volat integrovaným vývojovým prostředím, aby načítala soubory. Příznak jednoduše znamená, že rozhraní IDE nezobrazí položku nabídky Get a že modul plug-in není očekává poskytování uživatelského rozhraní.  
  
## <a name="rename-files-and-sccget"></a>Přejmenování souborů a sccget –  
 Situace: uživatel rezervuje soubor, například *a.txt*a změní ho. Před *a.txt* mohou být vráceny se změnami, druhý uživatel přejmenuje *a.txt* k *b.txt* v databázi správy zdrojových kódů, rezervuje *b.txt*, díky Některé úpravy k souboru a vrátí soubor. První uživatel chce, aby se změny provedené druhý uživatel, takže první uživatel přejmenuje jejich místní verzi *a.txt* do souboru *b.txt* a get v souboru. Předpokládá, ale stále místní mezipaměti, která uchovává informace o číslech verzí první verzi *a.txt* ukládají se místně a správy zdrojového kódu nemůže vyřešit rozdíly.  
  
 Existují dva způsoby, jak vyřešit tuto situaci, kde bude synchronizován s databázi správy zdrojových kódů místní mezipaměť verze ovládacího prvku zdroje:  
  
1.  Nepovolit přejmenování souboru v databázi správy zdrojových kódů, která je právě rezervována.  
  
2.  To ekvivalent "odstranit staré" následované "Přidat nový". Následující požadovaný algoritmus je jedním ze způsobů jak toho dosáhnout.  
  
    1.  Volání [sccquerychanges –](../extensibility/sccquerychanges-function.md) funkce, která se další informace o přejmenování *a.txt* k *b.txt* v databázi správy zdrojových kódů.  
  
    2.  Přejmenovat místní *a.txt* k *b.txt*.  
  
    3.  Volání `SccGet` funkce pro obě *a.txt* a *b.txt*.  
  
    4.  Protože *a.txt* neexistuje v databázi správy zdrojových kódů, se vyprazdňují místní verze mezipaměti chybí *a.txt* informace o verzi.  
  
    5.  *B.txt* soubor rezervuje se sloučí s obsahem místní *b.txt* souboru.  
  
    6.  Aktualizovaný *b.txt* souboru můžete teď být vráceny se změnami.  
  
## <a name="see-also"></a>Viz také:  
 [Funkce modulu plug-in API zdrojového ovládacího prvku](../extensibility/source-control-plug-in-api-functions.md)   
 [Příznaky Bitflag používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)
