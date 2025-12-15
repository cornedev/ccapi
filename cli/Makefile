CXX      := g++
CXXFLAGS := -std=c++17 -Wall -Wextra -O2

OBJ_DIR  := build
SRC := cli.cpp	ccapi_assets.cpp ccapi_process.cpp
OBJ      := $(SRC:%.cpp=$(OBJ_DIR)/%.o)

ICON_RC = gfx/icon.rc
ICON_OBJ = $(OBJ_DIR)/icon.o

TARGET := ccapi_cli

all: $(TARGET)

$(ICON_OBJ): $(ICON_RC) | build
	@mkdir -p $(dir $@)
	windres $< -O coff -o $@

$(TARGET): $(OBJ) $(ICON_OBJ)
	$(CXX) $(OBJ) $(ICON_OBJ) -o $@ -lwinhttp -lzip

$(OBJ_DIR)/%.o: %.cpp
	@mkdir -p $(OBJ_DIR)
	$(CXX) $(CXXFLAGS) -c $< -o $@

clean:
	rm -rf $(OBJ_DIR) $(TARGET)

run: all
	./$(TARGET)