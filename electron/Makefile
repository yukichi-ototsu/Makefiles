OS       = darwin
ARCH     = x64
BIN      = bin/
SRC      = src/
APP      = $(shell basename `pwd`)

COMPILER = electron
PACKAGER = electron-packager
APPEXEC  = open
MKDIR    = mkdir -p $(BIN) $(SRC)
TOUCH    = touch $(addprefix $(SRC),main.js index.html package.json) README.md
OUTDIR   = --out $(BIN)
PLATFORM = --platform=$(OS)
VERSION  = --version=$(shell electron -v | cut -c 2-)
ARCHOPT  = --arch=$(ARCH)
WRITE    = --overwrite
DEPEND   = $(wildcard $(SRC)*)
TARGET   = $(BIN)$(APP)-$(OS)-$(ARCH)

$(TARGET): $(DEPEND)
		$(PACKAGER) $(SRC) $(APP) $(OUTDIR) $(PLATFORM) $(WRITE) $(VERSION) $(ARCHOPT)

.PHONY : init
init:
		$(MKDIR)
		$(TOUCH)

.PHONY : all
all: clean $(TARGET)

.PHONY : run
run:
		$(COMPILER) $(SRS)

.PHONY : app-run
app-run:
		$(APPEXEC) $(TARGET)/$(APP).app

.PHONY : clean
clean:
		rm -f -r $(TARGET)
