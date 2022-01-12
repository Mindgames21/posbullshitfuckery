class CampMission extends SurvivorMissions
{
	//Mission related entities 
	TentBase MissionObject;
	FireplaceBase MissionCampfire;
	Object cc_fireplace;
	Object cc_mtent;
	Grenade_Base BoobyTrap;
    static ref BotMissions m_BotMInstanceDynamicSMM;
	
	//Mission parameters
	int MsgDlyFinish = 20;					//seconds, message delay time after player has finished mission
	
	//Mission containers
	ref array<vector> InfectedSpawns = new array<vector>;
	ref array<string> InfectedTypes = new array<string>;

	//Mission variables 
	string SurvivorName;		
	
	bool IsExtended() return false;
	
	void CampMission()
	{
		//Mission mission timeout
		m_MissionTimeout = 1200;			//seconds, mission duration time
		
		//Mission zones
		m_MissionZoneOuterRadius = 170.0;	//meters (!Do not set lower than 200m), mission activation distance
		m_MissionZoneInnerRadius = 3.0;		//meters (!Do not set outside of 1-5m), mission finishing distance to target object
				
		//Mission informant
		m_MissionInformant = "Dr. Legasov";
	
		//Mission person names
		TStringArray SurvivorNames = {"Yuri", "Michail", "Boris", "Valeri", "Anatoli", "Ivan", "Alexej", "Dimitrij", "Sergej", "Nikolai"};
		SurvivorName = SurvivorNames.GetRandomElement();
		
		//Set mission messages
        m_MissionMessage1 = "My friend "+ SurvivorName +" hasn't responded on the radio for last 2 hours. He is an excellent outdoor survivor and im wondering if he's ok.";
        m_MissionMessage2 = "His daughter is infected,  He looks after her sometimes. About 5 hours ago, he told me that he has found  stuff in some houses of "+ m_MissionLocation +" and was attacked on the way back to his camp but wasn't injured.";
        m_MissionMessage3 = "I think he said that he recently pitched up his tent\n "+ m_MissionLocationDir +" of "+ m_MissionLocation +" \nI am very worried, I would really appreciate it if you could go look after him. Be-Careful, he uses traps to protect his place!";		
/*				
		//Infected spawnpoints
		InfectedSpawns.Insert("-10.5186 0 25.0269");
		InfectedSpawns.Insert("24.9775 0 -10.4146");
		InfectedSpawns.Insert("-30.1726 0 -6.2729");
		InfectedSpawns.Insert("-20.9209 0 4.6636");
		InfectedSpawns.Insert("15.0283 0 -10.3276");
		InfectedSpawns.Insert("7.2461 0 30.5884");
		InfectedSpawns.Insert("-20.6855 0 5.9956");
		
		//Infected types
		//Male												//Female
		InfectedTypes.Insert("ZmbM_CitizenASkinny_Brown");	InfectedTypes.Insert("ZmbF_JournalistNormal_White");
		InfectedTypes.Insert("ZmbM_priestPopSkinny");		InfectedTypes.Insert("ZmbF_Clerk_Normal_White");
		InfectedTypes.Insert("ZmbM_HermitSkinny_Beige");	InfectedTypes.Insert("ZmbF_CitizenANormal_Blue");
		InfectedTypes.Insert("ZmbM_CitizenBFat_Red");		InfectedTypes.Insert("ZmbF_CitizenBSkinny");
		InfectedTypes.Insert("ZmbM_FishermanOld_Green");	InfectedTypes.Insert("ZmbF_HikerSkinny_Grey");
		InfectedTypes.Insert("ZmbM_HunterOld_Autumn");		InfectedTypes.Insert("ZmbF_SurvivorNormal_Orange");
		InfectedTypes.Insert("ZmbM_CitizenBFat_Blue");		InfectedTypes.Insert("ZmbF_HikerSkinny_Green");
		InfectedTypes.Insert("ZmbM_MotobikerFat_Black");	InfectedTypes.Insert("ZmbF_JoggerSkinny_Green");
		InfectedTypes.Insert("ZmbM_JoggerSkinny_Red");		InfectedTypes.Insert("ZmbF_SkaterYoung_Striped");
		InfectedTypes.Insert("ZmbM_MechanicSkinny_Grey");	InfectedTypes.Insert("ZmbF_BlueCollarFat_Red");
		InfectedTypes.Insert("ZmbM_HandymanNormal_Green");	InfectedTypes.Insert("ZmbF_MechanicNormal_Beige");
		InfectedTypes.Insert("ZmbM_HeavyIndustryWorker");	InfectedTypes.Insert("ZmbF_PatientOld");
		InfectedTypes.Insert("ZmbM_Jacket_black");			InfectedTypes.Insert("ZmbF_ShortSkirt_beige");
		InfectedTypes.Insert("ZmbM_Jacket_stripes");		InfectedTypes.Insert("ZmbF_VillagerOld_Red");
		InfectedTypes.Insert("ZmbM_HikerSkinny_Blue");		InfectedTypes.Insert("ZmbF_JoggerSkinny_Red");
		InfectedTypes.Insert("ZmbM_HikerSkinny_Yellow");	InfectedTypes.Insert("ZmbF_MilkMaidOld_Beige");
		InfectedTypes.Insert("ZmbM_PolicemanFat");			InfectedTypes.Insert("ZmbF_VillagerOld_Green");
		InfectedTypes.Insert("ZmbM_PatrolNormal_Summer");	InfectedTypes.Insert("ZmbF_ShortSkirt_yellow");
		InfectedTypes.Insert("ZmbM_JoggerSkinny_Blue");		InfectedTypes.Insert("ZmbF_NurseFat");
		InfectedTypes.Insert("ZmbM_VillagerOld_White");		InfectedTypes.Insert("ZmbF_PoliceWomanNormal");
		InfectedTypes.Insert("ZmbM_SkaterYoung_Brown");		InfectedTypes.Insert("ZmbF_HikerSkinny_Blue");
		InfectedTypes.Insert("ZmbM_MechanicSkinny_Green");	InfectedTypes.Insert("ZmbF_ParamedicNormal_Green");
		InfectedTypes.Insert("ZmbM_DoctorFat");				InfectedTypes.Insert("ZmbF_JournalistNormal_Red");
		InfectedTypes.Insert("ZmbM_PatientSkinny");			InfectedTypes.Insert("ZmbF_SurvivorNormal_White");
		InfectedTypes.Insert("ZmbM_ClerkFat_Brown");		InfectedTypes.Insert("ZmbF_JoggerSkinny_Brown");
		InfectedTypes.Insert("ZmbM_ClerkFat_White");		InfectedTypes.Insert("ZmbF_MechanicNormal_Grey");
		InfectedTypes.Insert("ZmbM_Jacket_magenta");		InfectedTypes.Insert("ZmbF_BlueCollarFat_Green");
		InfectedTypes.Insert("ZmbM_PolicemanSpecForce");	InfectedTypes.Insert("ZmbF_DoctorSkinny");
*/
	}

	void ~CampMission()
	{
		//Despawn all remaining mission objects
		if ( m_MissionObjects )
		{	
			Print("[SMM] Despawning "+ m_MissionObjects.Count() +" mission objects from old mission...");				
			for ( int i = 0; i < m_MissionObjects.Count(); i++ )
			{
				if ( !m_MissionObjects.Get(i) ) continue;
				else
				{
					//Delete Object clientside first
					if ( m_MissionObjects.Get(i).GetType() == "ClutterCutterFireplace" )
					GetGame().RemoteObjectDelete( m_MissionObjects.Get(i) );				
					
					//Delete Object serverside
					GetGame().ObjectDelete( m_MissionObjects.Get(i) );
				}		
			}
			m_MissionObjects.Clear();
		}
		
		//Despawn mission AI's
		if ( m_MissionAIs )
		{
			if ( m_MissionAIs.Count() > 0 )
			{
				Print("[SMM] Despawning "+ m_MissionAIs.Count() +" mission AI's from old mission...");
				for ( int k = 0; k < m_MissionAIs.Count(); k++ )
				{
					GetGame().ObjectDelete( m_MissionAIs.Get(k) );
				}
				m_MissionAIs.Clear();			
			}
			else Print("[SMM] No mission AI's to despawn.");
		}
		
		//Delete PlayersInZone list & reset container takeaway
		if ( m_PlayersInZone )	m_PlayersInZone.Clear();
		if ( m_ContainerWasTaken ) m_ContainerWasTaken = false;
	}
	
	void SpawnObjects()
	{				
		//Clean up place from droped items before new tent spawns 
		bool ItemsAtGround = false; 
		
		GetGame().GetObjectsAtPosition( m_MissionPosition , 4.0 , m_ObjectList , m_ObjectCargoList );
		for ( int i = 0 ; i < m_ObjectList.Count(); i++ )
		{ 
			Object FoundObject = m_ObjectList.Get(i);
			if ( FoundObject.IsItemBase() )
			{
				ItemsAtGround = true;
				Print("[SMM] BeforeSpawnCleanUp :: Object  " + FoundObject.ToString() + " at new mission position was deleted.");				
				GetGame().ObjectDelete( FoundObject );
			}
		}
		//...and in case move tent pos a bit
		if ( ItemsAtGround )
		{
			float x = Math.RandomFloatInclusive( 1.5 , 3.0 );
			float y = Math.RandomFloatInclusive( 1.5 , 3.0 );
			int Dice = Math.RandomIntInclusive( 0, 9);
			if ( Dice > 4 ) x *= -1.0;
			Dice = Math.RandomIntInclusive( 0, 9);
			if ( Dice < 5 ) y *= -1.0;
			vector NewPosVector = { x, 0, y };
			m_MissionPosition += NewPosVector;
			Print("[SMM] BeforeSpawnCleanUp :: Items on the ground detected. Tent position predictively was moved a bit.");
		}
		
		//Spawn & pitch tent		
		MissionObject = TentBase.Cast( GetGame().CreateObject( "MediumTent", m_MissionPosition ) );
		MissionObject.Pitch( true , true );
		MissionObject.PlaceOnSurface();
		
		//Get random loadout 
		int selectedLoadout = Math.RandomIntInclusive(0,9);	//!change randomization limit after adding new loadouts!	

		//Spawn selected loadout items in mission object
		EntityAI weapon;
				
		if (selectedLoadout == 0)
		{
			weapon = MissionObject.GetInventory().CreateInInventory("M4A1_Black");
				weapon.GetInventory().CreateAttachment("M4_RISHndgrd_Black");
				weapon.GetInventory().CreateAttachment("M4_MPBttstck");
				weapon.GetInventory().CreateAttachment("ACOGOptic");
				weapon.GetInventory().CreateAttachment("M4_Suppressor");
			MissionObject.GetInventory().CreateInInventory("Mag_STANAG_30Rnd");
			MissionObject.GetInventory().CreateInInventory("Mag_STANAG_30Rnd");
			MissionObject.GetInventory().CreateInInventory("M4_T3NRDSOptic");
			MissionObject.GetInventory().CreateInInventory("Ammo_556x45");
			MissionObject.GetInventory().CreateInInventory("Ammo_556x45");
			MissionObject.GetInventory().CreateInInventory("CanOpener");
			MissionObject.GetInventory().CreateInInventory("PeachesCan");
			MissionObject.GetInventory().CreateInInventory("Canteen");
			MissionObject.GetInventory().CreateInInventory("Battery9V");
		}
		if (selectedLoadout == 1)
		{
			weapon = MissionObject.GetInventory().CreateInInventory("SVD");
				weapon.GetInventory().CreateAttachment("PSO1Optic");
			MissionObject.GetInventory().CreateInInventory("Mag_SVD_10Rnd");
			MissionObject.GetInventory().CreateInInventory("Mag_SVD_10Rnd");
			MissionObject.GetInventory().CreateInInventory("PSO1Optic");
			MissionObject.GetInventory().CreateInInventory("KazuarOptic");
			MissionObject.GetInventory().CreateInInventory("Ammo_762x54");
			MissionObject.GetInventory().CreateInInventory("Ammo_762x54");
			MissionObject.GetInventory().CreateInInventory("Ammo_762x54");
			MissionObject.GetInventory().CreateInInventory("Ammo_762x54");
			MissionObject.GetInventory().CreateInInventory("Ammo_762x54");
			MissionObject.GetInventory().CreateInInventory("CanOpener");
			MissionObject.GetInventory().CreateInInventory("PeachesCan");
			MissionObject.GetInventory().CreateInInventory("Canteen");
			MissionObject.GetInventory().CreateInInventory("Battery9V");
		}
		if (selectedLoadout == 2)
		{
			weapon = MissionObject.GetInventory().CreateInInventory("AKM");
				weapon.GetInventory().CreateAttachment("AK_RailHndgrd_Green");
				weapon.GetInventory().CreateAttachment("AK_PlasticBttstck_Green");
				weapon.GetInventory().CreateAttachment("PSO1Optic");
				weapon.GetInventory().CreateAttachment("AK_Suppressor");
			MissionObject.GetInventory().CreateInInventory("Mag_AKM_30Rnd");
			MissionObject.GetInventory().CreateInInventory("Mag_AKM_30Rnd");
			MissionObject.GetInventory().CreateInInventory("Ammo_762x39");
			MissionObject.GetInventory().CreateInInventory("Ammo_762x39");
			MissionObject.GetInventory().CreateInInventory("Ammo_762x39");
			MissionObject.GetInventory().CreateInInventory("CanOpener");
			MissionObject.GetInventory().CreateInInventory("PeachesCan");
			MissionObject.GetInventory().CreateInInventory("Canteen");
			MissionObject.GetInventory().CreateInInventory("Battery9V");
		}
		if (selectedLoadout == 3)
		{
			weapon = MissionObject.GetInventory().CreateInInventory("FAL");
				weapon.GetInventory().CreateAttachment("Fal_OeBttstck");
			MissionObject.GetInventory().CreateInInventory("Mag_FAL_20Rnd");
			MissionObject.GetInventory().CreateInInventory("Mag_FAL_20Rnd");
			MissionObject.GetInventory().CreateInInventory("Mag_FAL_20Rnd");
			MissionObject.GetInventory().CreateInInventory("AK_Suppressor");
			MissionObject.GetInventory().CreateInInventory("ACOGOptic");
			MissionObject.GetInventory().CreateInInventory("FNX45");
			MissionObject.GetInventory().CreateInInventory("Mag_FNX45_15Rnd");
			MissionObject.GetInventory().CreateInInventory("Mag_FNX45_15Rnd");
			MissionObject.GetInventory().CreateInInventory("Ammo_45ACP");
			MissionObject.GetInventory().CreateInInventory("FNP45_MRDSOptic");
			MissionObject.GetInventory().CreateInInventory("PistolSuppressor");
			MissionObject.GetInventory().CreateInInventory("PsilocybeMushroom");
			MissionObject.GetInventory().CreateInInventory("AmmoBox");
			MissionObject.GetInventory().CreateInInventory("Battery9V");
		}	
		if (selectedLoadout == 4)
		{
			weapon = MissionObject.GetInventory().CreateInInventory("SKS");
				weapon.GetInventory().CreateAttachment("PUScopeOptic");
			MissionObject.GetInventory().CreateInInventory("Ammo_762x39");
			MissionObject.GetInventory().CreateInInventory("Ammo_762x39");
			weapon = MissionObject.GetInventory().CreateInInventory("FNX45");
				weapon.GetInventory().CreateAttachment("PistolSuppressor");
				EntityAI weaponlight = weapon.GetInventory().CreateAttachment("TLRLight");
					weaponlight.GetInventory().CreateAttachment("Battery9V");
			MissionObject.GetInventory().CreateInInventory("Mag_FNX45_15Rnd");
			MissionObject.GetInventory().CreateInInventory("Ammo_45ACP");
			MissionObject.GetInventory().CreateInInventory("AmmoBox");
		}	
		if (selectedLoadout == 5)
		{
			weapon = MissionObject.GetInventory().CreateInInventory("Winchester70");
				weapon.GetInventory().CreateAttachment("HuntingOptic");
			MissionObject.GetInventory().CreateInInventory("Ammo_308Win");
			MissionObject.GetInventory().CreateInInventory("Ammo_308Win");
			MissionObject.GetInventory().CreateInInventory("FNX45");
			MissionObject.GetInventory().CreateInInventory("Mag_FNX45_15Rnd");
			MissionObject.GetInventory().CreateInInventory("Ammo_45ACP");
			MissionObject.GetInventory().CreateInInventory("AmmoBox");
			MissionObject.GetInventory().CreateInInventory("PistolSuppressor");
			MissionObject.GetInventory().CreateInInventory("TLRLight");
			MissionObject.GetInventory().CreateInInventory("Battery9V");
		}
		if (selectedLoadout == 6)
		{			
			weapon = MissionObject.GetInventory().CreateInInventory("MP5K");
				weapon.GetInventory().CreateAttachment("MP5_RailHndgrd");
				weapon.GetInventory().CreateAttachment("MP5k_StockBttstck");
				weapon.GetInventory().CreateAttachment("M68Optic");
				weapon.GetInventory().CreateAttachment("PistolSuppressor");			
			MissionObject.GetInventory().CreateInInventory("Mag_MP5_30Rnd");
			MissionObject.GetInventory().CreateInInventory("Mag_MP5_30Rnd");
			MissionObject.GetInventory().CreateInInventory("AmmoBox_9x19_25rnd");
			MissionObject.GetInventory().CreateInInventory("GP5GasMask");
			MissionObject.GetInventory().CreateInInventory("NBCGlovesGray");
			MissionObject.GetInventory().CreateInInventory("WaterBottle");	
			MissionObject.GetInventory().CreateInInventory("SpaghettiCan");
			MissionObject.GetInventory().CreateInInventory("M18SmokeGrenade_Red");
			MissionObject.GetInventory().CreateInInventory("Battery9V");
			MissionObject.GetInventory().CreateInInventory("Battery9V");
			MissionObject.GetInventory().CreateInInventory("Battery9V");				
		}
		if (selectedLoadout == 7)
		{			
			weapon = MissionObject.GetInventory().CreateInInventory("AK74");
				weapon.GetInventory().CreateAttachment("AK_RailHndgrd");
				weapon.GetInventory().CreateAttachment("AK74_WoodBttstck");	
				weapon.GetInventory().CreateAttachment("KashtanOptic");
				weapon.GetInventory().CreateAttachment("'AK_Suppressor");			
			MissionObject.GetInventory().CreateInInventory("Mag_AK74_30Rnd");
			MissionObject.GetInventory().CreateInInventory("Mag_AK74_30Rnd");
			MissionObject.GetInventory().CreateInInventory("Headtorch_Grey");
			MissionObject.GetInventory().CreateInInventory("NBCBootsGray");
			MissionObject.GetInventory().CreateInInventory("Canteen");	
			MissionObject.GetInventory().CreateInInventory("TacticalBaconCan");
			MissionObject.GetInventory().CreateInInventory("Tomato");
			MissionObject.GetInventory().CreateInInventory("Battery9V");
			MissionObject.GetInventory().CreateInInventory("Battery9V");				
		}
		if (selectedLoadout == 8)
		{			
			weapon = MissionObject.GetInventory().CreateInInventory("AKS74U");
				weapon.GetInventory().CreateAttachment("AKS74U_Bttstck");			
			MissionObject.GetInventory().CreateInInventory("Mag_AK74_30Rnd");
			MissionObject.GetInventory().CreateInInventory("Mag_AK74_30Rnd");
			MissionObject.GetInventory().CreateInInventory("M67Grenade");
			MissionObject.GetInventory().CreateInInventory("M67Grenade");
			MissionObject.GetInventory().CreateInInventory("Matchbox");
			MissionObject.GetInventory().CreateInInventory("Canteen");	
			MissionObject.GetInventory().CreateInInventory("PortableGasStove");
			MissionObject.GetInventory().CreateInInventory("SmallGasCanister");
			MissionObject.GetInventory().CreateInInventory("Battery9V");
			MissionObject.GetInventory().CreateInInventory("Battery9V");
			MissionObject.GetInventory().CreateInInventory("Battery9V");			
		}
		if (selectedLoadout == 9)
		{			
			weapon = MissionObject.GetInventory().CreateInInventory("Glock19");
				weapon.GetInventory().CreateAttachment("PistolSuppressor");			
			MissionObject.GetInventory().CreateInInventory("Mag_Glock_15Rnd");
			MissionObject.GetInventory().CreateInInventory("Mag_Glock_15Rnd");
			MissionObject.GetInventory().CreateInInventory("FishingRod");
			MissionObject.GetInventory().CreateInInventory("Carp");
			MissionObject.GetInventory().CreateInInventory("Hook");
			MissionObject.GetInventory().CreateInInventory("Worm");
			MissionObject.GetInventory().CreateInInventory("CombatKnife");
			MissionObject.GetInventory().CreateInInventory("FieldShovel");
			MissionObject.GetInventory().CreateInInventory("Canteen");	
			MissionObject.GetInventory().CreateInInventory("MackerelFilletMeat");
			MissionObject.GetInventory().CreateInInventory("Battery9V");
			MissionObject.GetInventory().CreateInInventory("Battery9V");
			MissionObject.GetInventory().CreateInInventory("Battery9V");			
		}
			
		Print("[SMM] Mission rewards spawned in reward container. Randomly selected loadout was "+selectedLoadout+"." );
				
		//Insert mission tent into mission objects list
		m_MissionObjects.Insert( MissionObject );
	
		//Clutter Cutter Tent 	
		cc_mtent = GetGame().CreateObject( "MediumTentClutterCutter" , MissionObject.GetPosition() , false );
		cc_mtent.SetOrientation( MissionObject.GetOrientation() );
		GetGame().RemoteObjectCreate( cc_mtent );		 
		m_MissionObjects.Insert( cc_mtent );
		
		//Fireplace
		vector CampfirePosition;
		vector CampfireOrientation;
		vector CampFireDir = MissionObject.GetOrientation();
		float CampFireDist = 4;
			
		GetGame().ObjectDelete( cc_fireplace );
		GetGame().ObjectDelete( MissionCampfire );
		if ( CampFireDir[0] < 0 )	CampFireDir[0] = 360 + CampFireDir[0];
		//some nostalgic code 
		CampfirePosition [0] = m_MissionPosition [0] - Math.Sin( CampFireDir[0] * Math.DEG2RAD ) * CampFireDist;		//x offset
		CampfirePosition [2] = m_MissionPosition [2] - Math.Cos( CampFireDir[0] * Math.DEG2RAD ) * CampFireDist;		//y offset
		MissionCampfire = FireplaceBase.Cast( GetGame().CreateObject( "Fireplace", CampfirePosition ) );
		CampfireOrientation = MissionCampfire.GetOrientation();
		MissionCampfire.Synchronize();
		MissionCampfire.GetInventory().CreateAttachment("Firewood");
		MissionCampfire.GetInventory().CreateAttachment("WoodenStick");
		MissionCampfire.GetInventory().CreateAttachment("Rag");
		MissionCampfire.GetInventory().CreateAttachment("Stone");
		MissionCampfire.StartFire( true );
		m_MissionObjects.Insert( MissionCampfire );
		
		//Cluttercutter fireplace
		cc_fireplace = GetGame().CreateObject( "ClutterCutterFireplace" , MissionCampfire.GetPosition() );
		cc_fireplace.SetOrientation( CampfireOrientation );
		GetGame().RemoteObjectCreate( cc_fireplace );
		m_MissionObjects.Insert( cc_fireplace );
							
		Print("[SMM] Survivor Mission "+ m_selectedMission +" :: "+ m_MissionName +" ...mission deployed!");
	}
	
	void SpawnAIs()
	{	
		//Spawn dead infected
		vector InfectedPos = MissionObject.ModelToWorld( "0 0 -6" );
		m_MissionAIs.Insert( GetGame().CreateObject( "ZmbM_HikerSkinny_Blue" , InfectedPos , false , true ) );
		DayZInfected InfectedSurvivor = DayZInfected.Cast( m_MissionAIs[0] );
			InfectedSurvivor.GetInventory().CreateAttachment("FlatCap_Blue");
			InfectedSurvivor.GetInventory().CreateAttachment("MountainBag_Blue");
			InfectedSurvivor.GetInventory().CreateAttachment("UKAssVest_Black");
		EntityAI weapon1 = InfectedSurvivor.GetInventory().CreateInInventory("M4A1_Green");
				weapon1.GetInventory().CreateAttachment("M4_RISHndgrd_Green");
				weapon1.GetInventory().CreateAttachment("M4_MPBttstck");
				weapon1.GetInventory().CreateAttachment("ACOGOptic");
				weapon1.GetInventory().CreateAttachment("M4_Suppressor");
			InfectedSurvivor.GetInventory().CreateInInventory("Mag_STANAG_30Rnd");
			InfectedSurvivor.GetInventory().CreateInInventory("Mag_STANAG_30Rnd");
			InfectedSurvivor.GetInventory().CreateInInventory("M4_T3NRDSOptic");
			InfectedSurvivor.GetInventory().CreateInInventory("Ammo_556x45");
			InfectedSurvivor.GetInventory().CreateInInventory("Ammo_556x45");
			InfectedSurvivor.GetInventory().CreateInInventory("CanOpener");
			InfectedSurvivor.GetInventory().CreateInInventory("PeachesCan");
			InfectedSurvivor.GetInventory().CreateInInventory("Canteen");
			InfectedSurvivor.GetInventory().CreateInInventory("Battery9V");
				
			InfectedSurvivor.SetHealth("","",0);
		
		//Spawn boobytraped infected
		string RandomInfected = InfectedTypes.GetRandomElement();
		vector InfectedPos1 = MissionObject.ModelToWorld( "0 0 5" );
		
		m_MissionAIs.Insert( GetGame().CreateObject( RandomInfected, InfectedPos1, false, true ) );
		BoobyTrap = Grenade_Base.Cast( GetGame().CreateObject( "M67Grenade" , InfectedPos1, false, false, false ));
		BoobyTrap.ActivateImmediate();
		
		
		//Spawn infected
		for ( int j = 0 ; j < InfectedSpawns.Count() ; j++ )
		{
    	   	RandomInfected = InfectedTypes.GetRandomElement();
			InfectedPos1 = MissionObject.ModelToWorld( InfectedSpawns.Get(j) );
			m_MissionAIs.Insert( GetGame().CreateObject( RandomInfected, InfectedPos1, false, true ) );
		}

		//Spawn MissionGuards
        m_BotMInstanceDynamicSMM = new BotGroupMissionDynamicSMM();
        m_BotMInstanceDynamicSMM.StartMissionAI();

	}
	
	void ObjDespawn() 
	{	
		//Despawn all mission objects at mission timeout except those retains until next mission
		for ( int i = 0; i < m_MissionObjects.Count(); i++ )
		{
			//Exception: Fireplace & ClutterCutterFireplace will remain
			if ( m_MissionObjects.Get(i).GetType() == "Fireplace" || m_MissionObjects.Get(i).GetType() == "ClutterCutterFireplace" )	
			{
				Print("[SMM] "+ m_MissionObjects.Get(i).GetType() +" was excluded from pre-deletion.");
				continue;
			}
			
			//Delete Object clientside first
			if ( m_MissionObjects.Get(i).GetType() == "MediumTentClutterCutter" ) GetGame().RemoteObjectDelete( m_MissionObjects.Get(i) );
			
			//Delete Object serverside
			GetGame().ObjectDelete( m_MissionObjects.Get(i) );
		}
	}
	
	void MissionFinal()
	{	//When player enters last mission target zone	
		//Respawn some infected 
		for ( int j = 0 ; j < 2 ; j++ )
		{
    	   	string RandomInfected = InfectedTypes.GetRandomElement();
			vector InfectedPos = MissionObject.ModelToWorld( InfectedSpawns.GetRandomElement() );
			m_MissionAIs.Insert( GetGame().CreateObject( RandomInfected, InfectedPos, false, true ) );			
		}

		//Finish mission
		m_RewardsSpawned = true;
		m_MsgNum = -1;
		m_MsgChkTime = m_MissionTime + MsgDlyFinish;			
	}
	
	void PlayerChecks( PlayerBase player )
	{
		//Check if container gets taken from player
		if ( MissionSettings.Opt_DenyObjTakeaway )
		{		
			if ( m_MissionObjects[0] && m_MissionObjects[0].ClassName() == "MediumTent" ) 
			{
				if ( TentBase.Cast( m_MissionObjects[0] ).CanBeManipulated() && !m_ContainerWasTaken )
				{
					m_ContainerWasTaken = true;
					Print("[SMM] Mission tent was packed by a player ...and will be deleted.");
					GetGame().ObjectDelete( m_MissionObjects[0] );
				}
			}
		}	
	}
		
	void UpdateBots(float dt)
	{
		//Test1.OnUpdate(dt);		
	}
	
	bool DeployMission()
	{	//When first player enters the mission zone (primary/secondary)
		if ( m_MissionPosition && m_MissionPosition != "0 0 0" )
		{
			//Call spawners	
			GetGame().GetCallQueue( CALL_CATEGORY_GAMEPLAY ).Call( this.SpawnObjects );
			GetGame().GetCallQueue( CALL_CATEGORY_GAMEPLAY ).Call( this.SpawnAIs );
			return true;		
		}
		else 
		{
			Print("[SMM] ERROR : Mission position was rejected or doesn't exist. MissionPosition is NULL!");
			return false;
		}
	}
}


//----------------------------------------------------------------------------------------------------------------------------------
//------------------------------------- Custom AI Settings  --------------------------------------------------------
//----------------------------------------------------------------------------------------------------------------------------------
 
class BotGroupMissionDynamicSMM: MissionBase
{
    
    void BotGroupMissionDynamicSMM() {}
    
    
	// Bot configs
    vector MissionPosition = EventsWorldData.GetMissionPosition();
    vector BotSpawnPoint = MissionPosition - "-3 0 -3";              			// set the spawn point of the bot   
    
    int m_botAcuracy = 10;                                                      // Setting the bot's accuracy (the higher the number, the more often the bot misses)
    
    int BotSolderCountMin = 1;                                                  // assign the minimum number of bots
    int BotSolderCountMax = 1;                                                  // assign the maximum number of bots
    
    int botLootCountMin = 1;                                                    // set the minimum amount of loot for the bot
    int botLootCountMax = 1;                                                    // assign the maximum amount of loot for the bot
    
    float Zone_Radius = 300;                                                    // Trigger radius for the player to spawn bots
    
    bool isUseCheckPoints = true;                                               // set whether checkpoints are used true - used, fslse - not used
    bool isBotKaratist = false;                                                 // We set whether bots will carry weapons or will be fought with fists, by default they are with weapons, if needed without a firearm, write true
    bool onRespawnBot = false;                                                  // Enable or disable bot respawn (true - enabled, fslse - disabled)
    bool canUseTrigger = true;                                                  // Use trigger (true - enabled, fslse - disabled), if the trigger is not used, bots will spawn immediately after starting the server
    bool useKilFeed = true;                                                        // Enabling or disabling alerts when killing a bot
    bool m_Frendly = true;                                                     // Friendliness :) enable or disable. If enabled, then bots will not attack you until you attack it, if you attack a bot, you will become an enemy for all bots. 
    bool onVoice = true;                                                        // Enable or disable bot voice (enabling this setting causes more server load)
    int m_spawnBotRadius = 10;                                                 // The radius of the spawn of bots in the territory, the center of the territory is the coordinate specified in BotSpawnPoint
    int m_SpeedPatrol = 1;                                                      // Setting the movement speed while patrolling (min = 1 max = 3)
    
    
    int m_TargetDist = 25;                                                     // We set the distance in meters at which the bot sees the target.
    
    bool canBotSpawned = true;                                                  // Do not change !!!!!!!
    
    // ------------------------------- end of config  ------------------------------------------ //
    
    
    // ------------------------------- end of config  ------------------------------------------ //
    
    
    // Arrays with loot and clothes
    // If some type is not needed, just leave empty quotes example ---> TStringArray OtherEquip = {""}; 
 	ref TStringArray Shirt = {"GorkaEJacket_Autumn", "GorkaEJacket_Flat", "GorkaEJacket_PautRev", "GorkaEJacket_Summer"}; 					//Add the top of the clothes
	ref TStringArray Jeans = {"GorkaPants_Autumn", "GorkaPants_Flat", "GorkaPants_PautRev", "GorkaPants_Summer"}; 							//Add pants
	ref TStringArray Shoes = {"TTSKOBoots", "WorkingBoots_Beige", "CombatBoots_Beige", "CombatBoots_Black", "CombatBoots_Brown"};			//Add boots
	ref TStringArray BackPack = {"CoyoteBag_Brown", "CoyoteBag_Green", "HuntingBag", "TortillaBag", "WaterproofBag_Green"};					//Add the Backpack
	ref TStringArray Vest = {"HighCapacityVest_Black", "HighCapacityVest_Olive", "HuntingVest", "PlateCarrierVest", "UKAssVest_Camo"};		//Add Vest
	ref TStringArray Helm = {"GorkaHelmet", "Mich2001Helmet", "MotoHelmet_Black", "PumpkinHelmet", "SkateHelmet_Black"};					//Add a helmet or headgear
	ref TStringArray Gloves = {"WorkingGloves_Beige", "WorkingGloves_Black", "NBCGlovesGray", "OMNOGloves_Brown", "SurgicalGloves_Blue"};	//Add gloves
	ref TStringArray OtherEquip = {"CivilianBelt", "MilitaryBelt"};																			//Add an additional item of clothing, it can be anything :)	
	
	ref TStringArray RandomLoot = {"SardinesCan", "SodaCan_Cola", "SodaCan_Kvass", "Rice", "Rope", "Screwdriver", "AmmoBox_545x39_20Rnd"};  //We add any loot to the array, the amount is not limited
	ref TStringArray MeleeWeap = {"WoodAxe", "FirefighterAxe", "Shovel", "Pickaxe"}; 														//Add melee weapons
    
    // -------------------------------- end of loot arrays  -------------------------------------------------------//
 
    EntityAI itemEnt;               // Do not change !!!!
 
    // Function for creating checkpoints (register checkpoints here)
    void AddCeckPoint(SurvivorBotBase m_BotSolder)
    {
        m_BotSolder.SetUseCheckpoint(); // Эту строку не трогаем!
        
        
        m_BotSolder.AddCheckpoint( MissionPosition + "-5 0 -5");
        m_BotSolder.AddCheckpoint( MissionPosition + "5 0 5");
    //    m_BotSolder.AddCheckpoint( MissionPosition + "10 0 -10");
    //    m_BotSolder.AddCheckpoint( MissionPosition + "-5 0 -10");
    //    m_BotSolder.AddCheckpoint( MissionPosition + "-40 0 43");
    }
    // ---------------------------------- End of the function for creating checkpoints  -------------------------------------- / 
    
 
    ref array<SurvivorBotBase> m_BotMass = new array<SurvivorBotBase>;
    ref array<SurvivorBotBase> m_PlaersZoneArray = new array<SurvivorBotBase>;
    
	// The function of creating weapons for the bot (here you can add 7 weapon wmds, enter at your discretion)	
    void createWeapFromBot(SurvivorBotBase m_BotSolder)
    {
        int randomWeapon = Math.RandomInt(1, 7);
            
		switch( randomWeapon )
		{	
			case 1: 
			{
				m_BotSolder.AddWeapon("M4A1"); 				//Weapon
				m_BotSolder.AddWeaponAtt("M4_RISHndgrd");	//Att 1
				m_BotSolder.AddWeaponAtt("M4_MPBttstck");	//Att 2
				m_BotSolder.AddWeaponAtt("ACOGOptic");		//Att 3
				m_BotSolder.AddMagazine("Mag_STANAG_30Rnd"); //Mag
				break;
				//We add body kits as needed, magazines for weapons are issued automatically, no need to add them
			}
				
			case 2: 
			{
				m_BotSolder.AddWeapon("AKM");
				m_BotSolder.AddWeaponAtt("AK_WoodBttstck");
				m_BotSolder.AddWeaponAtt("AK_WoodHndgrd");
				m_BotSolder.AddMagazine("Mag_AKM_Drum75Rnd");
				break;
			}
				
			case 3: 
			{
				m_BotSolder.AddWeapon("AKM");
				m_BotSolder.AddWeaponAtt("AK_WoodBttstck");
				m_BotSolder.AddWeaponAtt("AK_WoodHndgrd");
				m_BotSolder.AddMagazine("Mag_AKM_Drum75Rnd");
				break;
			}
				
			case 4: 
			{
				m_BotSolder.AddWeapon("SVD");
				m_BotSolder.AddMagazine("Mag_SVD_10Rnd");
				break;
			}
				
			case 5: 
			{
				m_BotSolder.AddWeapon("M4A1"); 	
				m_BotSolder.AddWeaponAtt("M4_RISHndgrd");	
				m_BotSolder.AddWeaponAtt("M4_MPBttstck");	
				m_BotSolder.AddWeaponAtt("ACOGOptic");	
				m_BotSolder.AddMagazine("Mag_STANAG_30Rnd");
				break;
			}
				
			case 6: 
			{
				m_BotSolder.AddWeapon("AKM");
				m_BotSolder.AddWeaponAtt("AK_WoodBttstck");
				m_BotSolder.AddWeaponAtt("AK_WoodHndgrd");
				m_BotSolder.AddMagazine("Mag_AKM_Drum75Rnd");
				break;
			}
				
			case 7: 
			{
				m_BotSolder.AddWeapon("AKM");
				m_BotSolder.AddWeaponAtt("AK_WoodBttstck");
				m_BotSolder.AddWeaponAtt("AK_WoodHndgrd");
				m_BotSolder.AddMagazine("Mag_AKM_Drum75Rnd");
				break;
            }
        }       
    }
    // ----------------------------- End of weapon crafting function ------------------------------------- //
    
    // Bot spawn function (we don't change anything here !!!)
    void createBotUnit()
    {
        vector Navmesh;
        vector botSpPos;
        private SurvivorBotBase m_BotSolder;
        
        ref TStringArray m_BotBody = { "BotM_Mirek", "BotM_Rolf", "BotM_Quinn", "BotM_Peter", "BotM_Oliver" };
        
        PGFilter m_pgFilterNav = new PGFilter();
        m_pgFilterNav.SetFlags(PGPolyFlags.WALK, PGPolyFlags.INSIDE, 0);
        
        float bspX = BotSpawnPoint[0];
        float bspY = BotSpawnPoint[2];
                
        if (isUseCheckPoints)
            botSpPos = Vector(bspX + Math.RandomInt(-7, 7), BotSpawnPoint[1], bspY + Math.RandomInt(-7, 7));
        else
            botSpPos = Vector(bspX + Math.RandomInt(-m_spawnBotRadius, m_spawnBotRadius), BotSpawnPoint[1], bspY + Math.RandomInt(-m_spawnBotRadius, m_spawnBotRadius));
        
        bool IsNavmesh = world.SampleNavmeshPosition( botSpPos, 2, m_pgFilterNav, Navmesh );
        
        if (IsNavmesh)
            m_BotSolder = SurvivorBotBase.Cast(GetGame().CreatePlayer(null, m_BotBody.GetRandomElement(), Navmesh,  0, "NONE"));
        else
            m_BotSolder = SurvivorBotBase.Cast(GetGame().CreatePlayer(null, m_BotBody.GetRandomElement(), botSpPos,  0, "NONE"));
        
 
        m_BotSolder.GetInventory().CreateInInventory(Shirt.GetRandomElement());
        m_BotSolder.GetInventory().CreateInInventory(Jeans.GetRandomElement());
        m_BotSolder.GetInventory().CreateInInventory(Shoes.GetRandomElement());
        m_BotSolder.GetInventory().CreateInInventory(BackPack.GetRandomElement());
        m_BotSolder.GetInventory().CreateInInventory(Vest.GetRandomElement());
        m_BotSolder.GetInventory().CreateInInventory(Helm.GetRandomElement());
        m_BotSolder.GetInventory().CreateInInventory(Gloves.GetRandomElement());            
        m_BotSolder.GetInventory().CreateInInventory(OtherEquip.GetRandomElement());
        
        if (isBotKaratist)
            m_BotSolder.GetHumanInventory().CreateInHands(MeleeWeap.GetRandomElement());
        else
            createWeapFromBot(m_BotSolder);
            
        int rndLootCnt = Math.RandomInt(botLootCountMin, botLootCountMax);
            
        for (int i = 0; i < rndLootCnt; i++)
        {
            itemEnt = m_BotSolder.GetInventory().CreateInInventory(RandomLoot.GetRandomElement());
            if (itemEnt)
            {
                int rndHlt = Math.RandomInt(55,100);
                itemEnt.SetHealth("","",rndHlt);
            }
        }
 
        m_BotSolder.SetAcuracy(m_botAcuracy);
        m_BotSolder.SetDistance(m_TargetDist);
        m_BotSolder.SetUseVoice(onVoice);
        m_BotSolder.SetUseKillFeed(useKilFeed);
        m_BotSolder.SetFrendly(m_Frendly);
        m_BotSolder.SetSpeedPatrol(m_SpeedPatrol);
        
        
        if (isUseCheckPoints) 
            AddCeckPoint(m_BotSolder);
    
        
        m_BotMass.Insert(m_BotSolder);
    }
    // ----------------------------- end ------------------------------------- //
    
    // ----------------------------- Bots respawn function ----------------------------------------//
    private void respawnBotUnitDynamicSMM()
    {   
        ref array<Man> players = new array<Man>;
        GetGame().GetPlayers( players );
        SurvivorBotBase Bot_Ar;
        vector posB;
        bool m_botRemoved = false;
        float distB;
        int m_countBot = m_BotMass.Count();
        int plaersZoneCount = -1;
        m_PlaersZoneArray.Clear();
        if (canBotSpawned)
        {   
            for ( int u = 0; u < players.Count(); u++ )
            {
                    
                PlayerBase player;
                Class.CastTo(player, players.Get(u));
                vector pos = player.GetPosition();
                float dist = vector.Distance( pos, BotSpawnPoint );
                
                if ( dist < Zone_Radius && player.IsAlive() )
                {
                    m_PlaersZoneArray.Insert(player);
                //  return;
                }
            }   
            Print("Players count in zone bots DynamicSMM = " + m_PlaersZoneArray.Count());
            if (m_PlaersZoneArray.Count() == 0)
            {
                    
                for ( int a = 0; a < m_countBot; a++ )
                {
                    Bot_Ar = m_BotMass.Get(a);
                    if (Bot_Ar)
                    {
                        if (!Bot_Ar.IsAlive())
                        {
                            posB = Bot_Ar.GetPosition();
                            distB = vector.Distance( posB, BotSpawnPoint );
                            if (distB < Zone_Radius) 
                            {
                                m_BotMass.Remove( a );  
                            }
                            
                            if (m_BotMass.Count() == 0)
                                m_botRemoved = true;
                        }
                        else
                        {
                            if (distB < Zone_Radius) 
                            {
                                m_BotMass.Remove( a );  
                                GetGame().ObjectDelete( Bot_Ar );
                            }
                            
                            if (m_BotMass.Count() == 0)
                                m_botRemoved = true;
                        }
                    }
                }
                    
                if (m_botRemoved && m_PlaersZoneArray.Count() == 0) 
                {
                    StartMissionAI();
                    GetGame().GetCallQueue(CALL_CATEGORY_SYSTEM).Remove(respawnBotUnitDynamicSMM);
                    m_botRemoved = false;
                }
            }           
        }           
    }
    // ----------------------------- end ----------------------------------------//
    
 
    
    
    // Spawn function of a group of bots
    int delaySpawn = 0;
    void spawnBotGroup()
    {
        int rndBotGrpCnt = Math.RandomInt(BotSolderCountMin, BotSolderCountMax);
        Print("Bots spawned! Count " + rndBotGrpCnt);
        for (int a = 0; a < rndBotGrpCnt; a++)
        {
            GetGame().GetCallQueue(CALL_CATEGORY_SYSTEM).CallLater(createBotUnit, 500 + delaySpawn);
            delaySpawn +=1000;
        }   
    }
    // --------------------------------------- end  --------------------------------------- //
    
    // Player trigger function
    void TriggerPlayersDynamicSMM()
    {  
        ref array<Man> players = new array<Man>;
        GetGame().GetPlayers( players );
        delaySpawn = 0; 
        
        if (canBotSpawned && IsGoodSrvFps())
        {   
            for ( int u = 0; u < players.Count(); u++ )
            {
                    
                PlayerBase player;
                Class.CastTo(player, players.Get(u));
                vector pos = player.GetPosition();
                float dist = vector.Distance( pos, BotSpawnPoint );
                
                if ( dist < Zone_Radius && !player.IsBot() ) 
                {
                    spawnBotGroup();
                    GetGame().GetCallQueue(CALL_CATEGORY_SYSTEM).Remove(TriggerPlayersDynamicSMM);
                    
                    if (onRespawnBot)
                        GetGame().GetCallQueue(CALL_CATEGORY_SYSTEM).CallLater(respawnBotUnitDynamicSMM, 60000, true);                  
                } 
            }
        }
    } 
    // --------------------------------------- end  --------------------------------------- //
        
    void StartMissionAI()
    {
        Print("Start mission bot DynamicSMM");
        if (canUseTrigger)
        {
            GetGame().GetCallQueue(CALL_CATEGORY_SYSTEM).CallLater(TriggerPlayersDynamicSMM, 5000, true);           
        }
        else if (IsGoodSrvFps())
        {
            spawnBotGroup();
        }
    }
    
    bool IsGoodSrvFps()
    {
        float TestFpsSrv = GetGame().GetFps();
        
        if (TestFpsSrv < 2)
        {
            return true;
        }
        else
        {
            Print("Server FPS low! FPS = " + TestFpsSrv + " Bots not respawned!");
            return false;
        }           
    }
}
