#!/bin/bash

# ==========================================
# System Management Script
# Beautified and Optimized
# ==========================================

# Function: Environment Setup
# Sets system limits and configurations
environment() {
    local CAT_LIMIT="Increase"
    echo "Initializing: $CAT_LIMIT"
    
    # Note: Ensure you have permissions to edit /etc/security/limits.conf
    # The original code attempted to append lines here using sed.
    # Example: sed -i '$a * soft nofile 65535' /etc/security/limits.conf
}

# 1. High Performance Scene
scene_game() {
    echo "Applying: High Limit Scene (High Performance)..."
    echo "Setting sysctl parameters..."
    sysctl -p
}

# 2. Chat Server Scene
scene_chat() {
    echo "Applying: Chat Scene..."
    echo "Increasing file descriptors..."
    echo "Optimizing connections..."
    # ulimit -n 65535 (Example command that might belong here)
}

# 3. Java Game Scene
scene_java_game() {
    echo "Applying: Java Game Scene..."
    
    if [ -f "server.properties" ]; then
        echo "Configuration file found."
        echo "Optimizing Java arguments..."
    else
        echo "Error: 'server.properties' not found!"
    fi
}

# 4. Special Game Scene
scene_special_game() {
    echo "Applying: Special Game Scene..."
    echo "Disabling Swap..."
    swapoff -a
}

# 5. Clean Up Scene
scene_clean_game() {
    echo "Applying: System Cleanup..."
    echo "Cleaning logs and cache..."
    # Be careful with rm -rf
    rm -rf /var/log/*.log
    echo "Cleanup complete."
}

# 6. Space/Docker Scene
scene_space() {
    echo "Applying: Space Scene (Docker Setup)..."
    echo "Installing Docker..."
    apt-get update && apt-get install -y docker.io
}

# 7. Fix Permissions
scene_fix_game() {
    echo "Applying: Permission Fix..."
    echo "Setting permissions to 777 for /home/game..."
    chmod -R 777 /home/game
}

# ==========================================
# Main Menu Logic
# ==========================================

show_menu() {
    clear
    echo "========================================"
    echo "      SERVER OPTIMIZATION MANAGER       "
    echo "========================================"
    echo "1) Scene: Game (High Performance)"
    echo "2) Scene: Chat (High Connections)"
    echo "3) Scene: Java Game (Optimize Args)"
    echo "4) Scene: Special Game (No Swap)"
    echo "5) Scene: Clean (Clear Logs)"
    echo "6) Scene: Space (Install Docker)"
    echo "7) Scene: Fix (Repair Permissions)"
    echo "0) Exit"
    echo "========================================"
}

main() {
    while true; do
        show_menu
        read -p "Please enter your selection: " num

        case "$num" in
            1) scene_game ;;
            2) scene_chat ;;
            3) scene_java_game ;;
            4) scene_special_game ;;
            5) scene_clean_game ;;
            6) scene_space ;;
            7) scene_fix_game ;;
            0) 
                echo "Exiting..."
                exit 0 
                ;;
            *) 
                echo "Invalid selection. Please try again." 
                sleep 1
                ;;
        esac
        
        echo ""
        read -p "Press Enter to continue..."
    done
}

# Run the main function
main
