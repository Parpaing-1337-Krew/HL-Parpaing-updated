#
# Half-Life Full SDK 2.3 hl_i386.so Makefile for x86 Linux
#
# October 2002 by Leon Hartwig (hartwig@valvesoftware.com)
#

DLLNAME=hlp

ARCH=i386

#make sure this is the correct compiler for your system
CC=gcc

DLL_SRCDIR=.
ENGINE_SRCDIR=../engine
COMMON_SRCDIR=../common
PM_SHARED_SRCDIR=../pm_shared
GAME_SHARED_SRCDIR=../game_shared

DLL_OBJDIR=$(DLL_SRCDIR)/obj
PM_SHARED_OBJDIR=$(PM_SHARED_SRCDIR)/obj
GAME_SHARED_OBJDIR=$(GAME_SHARED_SRCDIR)/obj

BASE_CFLAGS=	-Dstricmp=strcasecmp -D_strnicmp=strncasecmp -Dstrnicmp=strncasecmp \
		-DCLIENT_WEAPONS

#safe optimization
CFLAGS=$(BASE_CFLAGS) -w -m486 -O1

#full optimization
#CFLAGS=$(BASE_CFLAGS) -w -O1 -m486 -ffast-math -funroll-loops \
	-fomit-frame-pointer -fexpensive-optimizations \
	-malign-loops=2 -malign-jumps=2 -malign-functions=2

#use these when debugging 
#CFLAGS=$(BASE_CFLAGS) -g

INCLUDEDIRS=-I. -I$(ENGINE_SRCDIR) -I$(COMMON_SRCDIR) -I$(PM_SHARED_SRCDIR) -I$(GAME_SHARED_SRCDIR)

LDFLAGS=

SHLIBEXT=so
SHLIBCFLAGS=-fPIC
SHLIBLDFLAGS=-shared

DO_CC=$(CC) $(CFLAGS) $(SHLIBCFLAGS) $(INCLUDEDIRS) -o $@ -c $<

#############################################################################
# SETUP AND BUILD
# GAME
#############################################################################

$(DLL_OBJDIR)/%.o: $(DLL_SRCDIR)/%.cpp
	$(DO_CC)

$(GAME_SHARED_OBJDIR)/%.o: $(GAME_SHARED_SRCDIR)/%.cpp
	$(DO_CC)

$(PM_SHARED_OBJDIR)/%.o: $(PM_SHARED_SRCDIR)/%.c
	$(DO_CC)

OBJ = \
	$(DLL_OBJDIR)/airtank.o \
	$(DLL_OBJDIR)/animating.o \
	$(DLL_OBJDIR)/animation.o \
	$(DLL_OBJDIR)/auto-help.o \
	$(DLL_OBJDIR)/bar.o \
	$(DLL_OBJDIR)/barney.o \
	$(DLL_OBJDIR)/bigmomma.o \
	$(DLL_OBJDIR)/bmodels.o \
	$(DLL_OBJDIR)/bullsquid.o \
	$(DLL_OBJDIR)/buttons.o \
	$(DLL_OBJDIR)/carnet.o \
	$(DLL_OBJDIR)/cbase.o \
	$(DLL_OBJDIR)/client.o \
	$(DLL_OBJDIR)/combat.o \
	$(DLL_OBJDIR)/crowbar.o \
	$(DLL_OBJDIR)/ctf.o \
	$(DLL_OBJDIR)/dayofparpaing.o \
	$(DLL_OBJDIR)/defaultai.o \
	$(DLL_OBJDIR)/defuse_the_parpaing.o \
	$(DLL_OBJDIR)/doors.o \
	$(DLL_OBJDIR)/effects.o \
	$(DLL_OBJDIR)/explode.o \
	$(DLL_OBJDIR)/flyingmonster.o \
	$(DLL_OBJDIR)/func_break.o \
	$(DLL_OBJDIR)/func_tank.o \
	$(DLL_OBJDIR)/game.o \
	$(DLL_OBJDIR)/gamerules.o \
	$(DLL_OBJDIR)/genericmonster.o \
	$(DLL_OBJDIR)/ggrenade.o \
	$(DLL_OBJDIR)/globals.o \
	$(DLL_OBJDIR)/h_ai.o \
	$(DLL_OBJDIR)/h_battery.o \
	$(DLL_OBJDIR)/h_cine.o \
	$(DLL_OBJDIR)/h_cycler.o \
	$(DLL_OBJDIR)/h_export.o \
	$(DLL_OBJDIR)/healthkit.o \
	$(DLL_OBJDIR)/hlpsound.o \
	$(DLL_OBJDIR)/items.o \
	$(DLL_OBJDIR)/lights.o \
	$(DLL_OBJDIR)/maprules.o \
	$(DLL_OBJDIR)/megret.o \
	$(DLL_OBJDIR)/monstermaker.o \
	$(DLL_OBJDIR)/monsters.o \
	$(DLL_OBJDIR)/monsterstate.o \
	$(DLL_OBJDIR)/mortar.o \
	$(DLL_OBJDIR)/multiplay_gamerules.o \
	$(DLL_OBJDIR)/mur_parpaing.o \
	$(DLL_OBJDIR)/nodes.o \
	$(DLL_OBJDIR)/parpaing.o \
	$(DLL_OBJDIR)/pathcorner.o \
	$(DLL_OBJDIR)/plane.o \
	$(DLL_OBJDIR)/plats.o \
	$(DLL_OBJDIR)/player.o \
	$(DLL_OBJDIR)/rat.o \
	$(DLL_OBJDIR)/roach.o \
	$(DLL_OBJDIR)/schedule.o \
	$(DLL_OBJDIR)/scientist.o \
	$(DLL_OBJDIR)/scripted.o \
	$(DLL_OBJDIR)/sifflet2.o \
	$(DLL_OBJDIR)/singleplay_gamerules.o \
	$(DLL_OBJDIR)/skill.o \
	$(DLL_OBJDIR)/sound.o \
	$(DLL_OBJDIR)/soundent.o \
	$(DLL_OBJDIR)/special_parpaing.o \
	$(DLL_OBJDIR)/spectator.o \
	$(DLL_OBJDIR)/sqlfunc.o \
	$(DLL_OBJDIR)/squadmonster.o \
	$(DLL_OBJDIR)/subs.o \
	$(DLL_OBJDIR)/talkmonster.o \
	$(DLL_OBJDIR)/teamplay_gamerules.o \
	$(DLL_OBJDIR)/tempmonster.o \
	$(DLL_OBJDIR)/tentacle.o \
	$(DLL_OBJDIR)/triggers.o \
	$(DLL_OBJDIR)/turret.o \
	$(DLL_OBJDIR)/util.o \
	$(DLL_OBJDIR)/weapons.o \
	$(DLL_OBJDIR)/world.o \
	$(DLL_OBJDIR)/xen.o \
	$(GAME_SHARED_OBJDIR)/voice_gamemgr.o \
	$(PM_SHARED_OBJDIR)/pm_debug.o \
	$(PM_SHARED_OBJDIR)/pm_math.o \
	$(PM_SHARED_OBJDIR)/pm_shared.o

$(DLLNAME)_$(ARCH).$(SHLIBEXT) : neat $(OBJ)
	$(CC) $(CFLAGS) $(SHLIBLDFLAGS) $(LDFLAGS) -o $@ $(OBJ)

neat:
	-mkdir $(DLL_OBJDIR)
	-mkdir $(GAME_SHARED_OBJDIR)
	-mkdir $(PM_SHARED_OBJDIR)
clean:
	-rm -f $(OBJ)
	-rm -f $(DLLNAME)_$(ARCH).$(SHLIBEXT)
spotless: clean
	-rm -r $(DLL_OBJDIR)
	-rm -r $(GAME_SHARED_OBJDIR)
	-rm -r $(PM_SHARED_OBJDIR)
